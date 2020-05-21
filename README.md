# 설치하기

## 1. 필요한 패키지 설치

Github 페이지에 있는 tripwire 를 다운로드 하기 위한 wget 패키지를 설치합니다.

```text
# yum -y install wget
```

tripwire 소스를 컴파일 하기 위한 gcc / gcc-c++ 패키지를 설치합니다.

```
# yum -y install gcc gcc-c++
```

## 2. 다운로드 및 압축풀

wget 명령어를 이용하여 tripwire 소스를 Github에서 다운받습니다.

```text
# wget https://github.com/Tripwire/tripwire-open-source/releases/download/2.4.3.7/tripwire-open-source-2.4.3.7.tar.gz
```

다운받은 소스의 압축을 풀고, 생성된 폴더로 이동합니다.

```text
# tar -zxvf tripwire-open-source-2.4.3.7.tar.gz
# cd ./tripwire-open-source-2.4.3.7
```

## 3. Configure 파일 설정

기본 경로로 설치하기를 원한다면 --prefix 옵션 없이 Configure 파일을 실행합니다.

```text
# ./configure
```

별도로 설치하고싶은 경로가 있다면 --prefix 옵션을 통해 경로를 지정해줍니다.

```text
# ./configure --prefix=[Install folder path]
```

## 4. 소스 컴파일

make , make install 명령어를 통해서 소를 컴파일 합니다.

```text
# make
# make install
```

## 5. TWREPORT 경로 변경하기

twcfg.txt 설정파일을 twcfg.txt.back 파일로 복사해서 백업을 합니다.

```text
# cp [Install folder path]/etc/twcfg.txt [Install folder path]/etc/twcfg.txt.back
```

twcfg.txt 설정파일에서 REPORTFILE 이 저장될 경로를 원하는 경로로 변경합니다.   
예\) /usr/azman/report/

```text
# cp [Install folder path]/etc/twcfg.txt [Install folder path]/etc/twcfg.txt.back
# cat [Install folder path]/etc/twcfg.txt | sed 's/REPORTFILE[ ]*[=/a-zA-Z]*/REPORTFILE    =\/usr\/azman\/report\//g' >> [Install folder path]/etc/twcfg.txt
```

수정된 twcfg.txt 파일을 반영합니다.

```text
# [Install folder path]/sbin/twadmin --create-cfgfile -S [Install folder path]/etc/site.key [Install folder path]/etc/twcfg.txt
```

## 6. Rule 생성하기

```text
# vi [Install folder path]/etc/twpol.txt
```

전역으로 사용할 변수를 설정합니다. TWREPORT 는 twcfg.txt 에서 변경한 경로와 동일하게 지정해 줍니다.

```bash
# Global Variable Definitions
#@@section GLOBAL

TWROOT   = "[Install folder path]/sbin";
TWBIN    = "[Install folder path]/sbin";
TWPOL    = "[Install folder path]/etc";
TWDB     = "[Install folder path]/lib/tripwire/azvdi3.twd";
TWSKEY   = "[Install folder path]/etc";
TWLKEY   = "[Install folder path]/etc";
TWREPORT = "/usr/azman/report";      # 위에서 지정한 경로로 변
```



### 6.1 파일의 중요도 및 특성을 표현하는 속성

| No | Attribute | Value | Description |
| :---: | :---: | :---: | :--- |
| 1 | file or folder | SEC\_CRIT | 변경할 수 없는 중요 파일 |
| 2 | file or folder | SEC\_SUID | SUID 또는 SGID 플래그가 설정된 바이너리 파일 |
| 3 | file or folder | SEC\_BIN | 변경할 수 없는 바이너리 파 |
| 4 | file or folder | SEC\_CONFIG | Config files that are changed infrequently but accessed often |
| 5 | file or folder | SEC\_LOG | Files that grow, but that should never change |
| 6 | file or folder | SEC\_INVARIANT | Directories that should never change permission |

```bash
#@@section FS
SEC_CRIT      = $(IgnoreNone)-SHa ;  # Critical files that cannot change
SEC_SUID      = $(IgnoreNone)-SHa ;  # Binaries with the SUID or SGID flags set
SEC_BIN       = $(ReadOnly) ;        # Binaries that should not change
SEC_CONFIG    = $(Dynamic) ;         # Config files that are changed infrequently but accessed often
SEC_LOG       = $(Growing) ;         # Files that grow, but that should never change ownership
SEC_INVARIANT = +tpug ;              # Directories that should never change permission or ownership
SIG_LOW       = 33 ;                 # Non-critical files that are of minimal security impact
SIG_MED       = 66 ;                 # Non-critical files that are of significant security impact
SIG_HI        = 100 ;                # Critical files that are significant points of vulnerability
```



### 6.2 Custom Rule Format

| No | Attribute | Value | Description |
| :---: | :---: | :---: | :--- |
| 1 | rulename | "Rule Name" | Just rule name |
| 2 | severity | SIG\_HI | Critical files that are significant points of vulnerability |
| 3 | severity | SIG\_MED | Non-critical files that are of significant security |
| 4 | severity | SIG\_LOG | Non-critical files that are of minimal security impact |

```bash
# My Rule
(
    rulename = "My Rule",
    severity = $(SIG_HI|SIG_MED|SIG_LOW)
)
{
    /home/tripwire/crit      -> $(SEC_CRIT);
    /home/tripwire/suid      -> $(SEC_SUID);
    /home/tripwire/bin       -> $(SEC_BIN);
    /home/tripwire/config    -> $(SEC_CONFIG);
    /home/tripwire/log       -> $(SEC_LOG);
    /home/tripwire/invariant -> $(SEC_INVARIANT);
}
```

## 7. Generate Database

```css
cd [Install folder path]/sbin
./twadmin -m P [Install folder path]/etc/twpol.txt
./tripwire --init
```

## 8. Check

```text
cd [Install folder path]/sbin
./tripwire --check
```

