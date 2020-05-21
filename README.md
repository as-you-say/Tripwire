# 설치하기

## 파라미터

\[Install folder path\] : Tripwire 를 설치할 폴더 경로

\[Report folder path\] : Tripwire 레포트를 저장할 폴더 경로

## 1. 필요한 패키지 설치

**Github** 페이지에 있는 **tripwire** 를 다운로드 하기 위한 **wget** 패키지를 설치합니다.

```text
# yum -y install wget
```

**tripwire** 소스를 컴파일 하기 위한 **gcc / gcc-c++** 패키지를 설치합니다.

```
# yum -y install gcc gcc-c++
```

## 2. 다운로드 및 압축풀기

**wget** 명령어를 이용하여 **tripwire** 소스를 **Github**에서 다운받습니다.

{% embed url="https://github.com/Tripwire/tripwire-open-source/releases/download/2.4.3.7/tripwire-open-source-2.4.3.7.tar.gz" %}

```text
# wget https://github.com/Tripwire/tripwire-open-source/releases/download/2.4.3.7/tripwire-open-source-2.4.3.7.tar.gz
```

다운받은 소스의 압축을 풀고, 생성된 폴더로 이동합니다.

```text
# tar -zxvf tripwire-open-source-2.4.3.7.tar.gz
# cd ./tripwire-open-source-2.4.3.7
```

## 3. Configure 파일 설정 \(둘중 하나 선택\)

기본 경로로 설치하기를 원한다면 **--prefix** 옵션 없이 Configure 파일을 실행합니다.  
**기본경로 : /usr/local**

```text
# ./configure
```

별도로 설치하고싶은 경로가 있다면 **--prefix** 옵션을 통해 경로를 지정해줍니다.  
예\) \[Install folder path\] : /usr/local/test

```text
# ./configure --prefix=[Install folder path]
```

## 4. 소스 컴파일

**make , make install** 명령어를 통해서 소를 컴파일 합니다.

```text
# make
# make install
```

아래와 같은 내용이 나오면 **Enter 키**를 눌러줍니다.

```text
Making install in man
make[1]: Entering directory `/home/tripwire/tripwire-open-source-2.4.3.7/man'
Making install in man4
make[2]: Entering directory `/home/tripwire/tripwire-open-source-2.4.3.7/man/man4'
make[3]: Entering directory `/home/tripwire/tripwire-open-source-2.4.3.7/man/man4'
make[3]: `install-exec-am'를 위해 할 일이 없습니다
 /usr/bin/mkdir -p '/usr/local/share/man/man4'
 /usr/bin/install -c -m 644 twconfig.4 twpolicy.4 '/usr/local/share/man/man4'
make[3]: Leaving directory `/home/tripwire/tripwire-open-source-2.4.3.7/man/man4'
make[2]: Leaving directory `/home/tripwire/tripwire-open-source-2.4.3.7/man/man4'
Making install in man5
make[2]: Entering directory `/home/tripwire/tripwire-open-source-2.4.3.7/man/man5'
make[3]: Entering directory `/home/tripwire/tripwire-open-source-2.4.3.7/man/man5'
make[3]: `install-exec-am'를 위해 할 일이 없습니다
 /usr/bin/mkdir -p '/usr/local/share/man/man5'
 /usr/bin/install -c -m 644 twfiles.5 '/usr/local/share/man/man5'
make[3]: Leaving directory `/home/tripwire/tripwire-open-source-2.4.3.7/man/man5'
make[2]: Leaving directory `/home/tripwire/tripwire-open-source-2.4.3.7/man/man5'
Making install in man8
make[2]: Entering directory `/home/tripwire/tripwire-open-source-2.4.3.7/man/man8'
make[3]: Entering directory `/home/tripwire/tripwire-open-source-2.4.3.7/man/man8'
make[3]: `install-exec-am'를 위해 할 일이 없습니다
 /usr/bin/mkdir -p '/usr/local/share/man/man8'
 /usr/bin/install -c -m 644 siggen.8 tripwire.8 twadmin.8 twintro.8 twprint.8 '/usr/local/share/man/man8'
make[3]: Leaving directory `/home/tripwire/tripwire-open-source-2.4.3.7/man/man8'
make[2]: Leaving directory `/home/tripwire/tripwire-open-source-2.4.3.7/man/man8'
make[2]: Entering directory `/home/tripwire/tripwire-open-source-2.4.3.7/man'
make[3]: Entering directory `/home/tripwire/tripwire-open-source-2.4.3.7/man'
make[3]: `install-exec-am'를 위해 할 일이 없습니다
make[3]: `install-data-am'를 위해 할 일이 없습니다
make[3]: Leaving directory `/home/tripwire/tripwire-open-source-2.4.3.7/man'
make[2]: Leaving directory `/home/tripwire/tripwire-open-source-2.4.3.7/man'
make[1]: Leaving directory `/home/tripwire/tripwire-open-source-2.4.3.7/man'
Making install in src
make[1]: Entering directory `/home/tripwire/tripwire-open-source-2.4.3.7/src'
true
make[1]: Leaving directory `/home/tripwire/tripwire-open-source-2.4.3.7/src'
make[1]: Entering directory `/home/tripwire/tripwire-open-source-2.4.3.7'
make[2]: Entering directory `/home/tripwire/tripwire-open-source-2.4.3.7'
make[2]: `install-exec-am'를 위해 할 일이 없습니다
make  install-data-hook
make[3]: Entering directory `/home/tripwire/tripwire-open-source-2.4.3.7'
INSTALL_STRIP_FLAG="" \
prefix="/usr/local" sysconfdir="/usr/local/etc" \
path_to_vi="/usr/bin/vi" path_to_sendmail="/usr/sbin/sendmail" \
./installer/install.sh

Installer program for:
Tripwire(R) 2.4 Open Source

Copyright (C) 1998-2017 Tripwire, Inc.
Tripwire is a registered trademark of Tripwire, Inc. All rights reserved.


LICENSE AGREEMENT for Tripwire(R) 2.4 Open Source

Please read the following license agreement.  You must accept the
agreement to continue installing Tripwire.

Press ENTER to view the License Agreement.
```

**Enter 키**를 누르고 나면, 아래와 같이 라이센스 동의에 관한 문서가 출력됩니다.

**q 키**를 눌러줍니다.

```text
                    GNU GENERAL PUBLIC LICENSE                                
                       Version 2, June 1991                                   
                                                                              
 Copyright (C) 1989, 1991 Free Software Foundation, Inc.                      
                       59 Temple Place, Suite 330, Boston, MA  02111-1307  USA
 Everyone is permitted to copy and distribute verbatim copies                 
 of this license document, but changing it is not allowed.                    
                                                                              
                            Preamble                                          
                                                                              
  The licenses for most software are designed to take away your               
freedom to share and change it.  By contrast, the GNU General Public          
License is intended to guarantee your freedom to share and change free        
software--to make sure the software is free for all its users.  This          
General Public License applies to most of the Free Software                   
Foundation's software and to any other program whose authors commit to        
using it.  (Some other Free Software Foundation software is covered by        
the GNU Library General Public License instead.)  You can apply it to         
your programs, too.                                                           
                                                                              
  When we speak of free software, we are referring to freedom, not            
price.  Our General Public Licenses are designed to make sure that you        
have the freedom to distribute copies of free software (and charge for        
this service if you wish), that you receive source code or can get it         
if you want it, that you can change the software or use pieces of it          
in new free programs; and that you know you can do these things.              
                                                                              
  To protect your rights, we need to make restrictions that forbid            
anyone to deny you these rights or to ask you to surrender the rights.        
These restrictions translate to certain responsibilities for you if you       
distribute copies of the software, or if you modify it.                       
                                                                              
  For example, if you distribute copies of such a program, whether            
gratis or for a fee, you must give the recipients all the rights that         
you have.  You must make sure that they, too, receive or can get the          
source code.  And you must show them these terms so they know their           
rights.                                                                       
                                                                              
  We protect your rights with two steps: (1) copyright the software, and      
(2) offer you this license which gives you legal permission to copy,          
distribute and/or modify the software.                                        
                                                                              
  Also, for each author's protection and ours, we want to make certain        
that everyone understands that there is no warranty for this free             
software.  If the software is modified by someone else and passed on, we      
want its recipients to know that what they have is not the original, so       
that any problems introduced by others will not reflect on the original       
authors' reputations.                                                         
                                                                              
  Finally, any free program is threatened constantly by software              
patents.  We wish to avoid the danger that redistributors of a free           
program will individually obtain patent licenses, in effect making the        
program proprietary.  To prevent this, we have made it clear that any         
patent must be licensed for everyone's free use or not licensed at all.       
                                                                              
:q                                                                             
```

라이센스 동의에 관한 문서를 빠져나온 후, **accept** 라는 문자를 입력한 후 **Enter 키**를 눌러줍니다.

```text
Press ENTER to view the License Agreement.



Please type "accept" to indicate your acceptance of this
license agreement. [do not accept] accept
```

설치를 계속 하실건지 물어보면, **y** 를 입력 후 **Enter 키**를 눌러줍니다.

```text
Using configuration file ./installer/install.cfg

Checking for programs specified in install configuration file....

/usr/sbin/sendmail -oi -t exists.  Continuing installation.

/usr/bin/vi exists.  Continuing installation.


----------------------------------------------
Verifying existence of binaries...

./bin/siggen found
./bin/tripwire found
./bin/twprint found
./bin/twadmin found

This program will copy Tripwire files to the following directories:

        TWBIN: /usr/local/sbin
        TWMAN: /usr/local/man
     TWPOLICY: /usr/local/etc
     TWREPORT: /usr/local/lib/tripwire/report
         TWDB: /usr/local/lib/tripwire
 TWSITEKEYDIR: /usr/local/etc
TWLOCALKEYDIR: /usr/local/etc

CLOBBER is false.

Continue with installation? [y/n] y
```

설치 경로에 필요한 파일 및 폴더가 생성된 후, **site 비밀번호**를 설정합니다.

원하는 **site 비밀번호**를 설정합니다. ex\) site

원하는 **local 비밀번호**를 설정합니다 ex\) local

```text
----------------------------------------------
Creating directories...

/usr/local/sbin: already exists
/usr/local/etc: already exists
/usr/local/lib/tripwire/report: already exists
/usr/local/lib/tripwire: already exists
/usr/local/etc: already exists
/usr/local/etc: already exists
/usr/local/man: already exists
/usr/local/doc/tripwire: already exists

----------------------------------------------
Copying files...

/usr/local/doc/tripwire/COPYING: file already exists
/usr/local/sbin/tripwire: file already exists
/usr/local/sbin/twadmin: file already exists
/usr/local/sbin/twprint: file already exists
/usr/local/sbin/siggen: file already exists
/usr/local/doc/tripwire/TRADEMARK: file already exists
/usr/local/doc/tripwire/policyguide.txt: file already exists
/usr/local/etc/twpol-Linux.txt: copied
/usr/local/doc/tripwire/COMMERCIAL: file already exists
/usr/local/doc/tripwire/ReadMe-2.4.3: file already exists
/usr/local/doc/tripwire/ChangeLog: file already exists

----------------------------------------------
The Tripwire site and local passphrases are used to
sign a variety of files, such as the configuration,
policy, and database files.

Passphrases should be at least 8 characters in length
and contain both letters and numbers.

See the Tripwire manual for more information.

----------------------------------------------
Creating key files...

(When selecting a passphrase, keep in mind that good passphrases typically
have upper and lower case letters, digits and punctuation marks, and are
at least 8 characters in length.)

Enter the site keyfile passphrase: [원하는 site 비밀번호]
Verify the site keyfile passphrase: [원하는 site 비밀번]
Generating key (this may take several minutes)...Key generation complete.

(When selecting a passphrase, keep in mind that good passphrases typically
have upper and lower case letters, digits and punctuation marks, and are
at least 8 characters in length.)

Enter the local keyfile passphrase: [원하는 local 비밀번호]
Verify the local keyfile passphrase: [원하는 local 비밀번]

```

위에서 설정한 **site 비밀번호**를 한번 더 입력한 후 **Enter 키**를 눌러줍니다.

```text
Generating key (this may take several minutes)...Key generation complete.

----------------------------------------------
Generating Tripwire configuration file...

----------------------------------------------
Creating signed configuration file...
Please enter your site passphrase:
```

설치가 성공하였다는 메시지를 확인할 수 있습니다!  
The installation succeded.

```text
Wrote policy file: /usr/local/etc/tw.pol

A clear-text version of the Tripwire policy file
/usr/local/etc/twpol.txt
has been preserved for your inspection.  This implements
a minimal policy, intended only to test essential
Tripwire functionality.  You should edit the policy file
to describe your system, and then use twadmin to generate
a new signed copy of the Tripwire policy.


----------------------------------------------
The installation succeeded.

Please refer to documentation in /usr/local/doc/tripwire
for release information and to the printed user documentation
for further instructions on using Tripwire 2.4 Open Source.

make[3]: Leaving directory `/home/tripwire/tripwire-open-source-2.4.3.7'
make[2]: Leaving directory `/home/tripwire/tripwire-open-source-2.4.3.7'
make[1]: Leaving directory `/home/tripwire/tripwire-open-source-2.4.3.7'
```

## 5. TWREPORT 경로 변경하기

twcfg.txt 설정파일을 twcfg.txt.back 파일로 복사해서 백업을 합니다.

```scheme
# cp [Install folder path]/etc/twcfg.txt [Install folder path]/etc/twcfg.txt.back
```

twcfg.txt 설정파일에서 REPORTFILE 이 저장될 경로를 원하는 경로로 변경합니다. 

```bash
ROOT          =[Install folder path]/sbin
POLFILE       =[Install folder path]/etc/tw.pol

# 데이터베이스 파일 경로
DBFILE        =[Install folder path]/lib/tripwire/$(HOSTNAME).twd

# 레포트 경로
REPORTFILE    =/usr/helloman/report/$(HOSTNAME)-$(DATE).twr

SITEKEYFILE   =[Install folder path]/etc/site.key
LOCALKEYFILE  =[Install folder path]/etc/localhost.localdomain-local.key
EDITOR        =/usr/bin/vi
LATEPROMPTING =false
LOOSEDIRECTORYCHECKING =false
MAILNOVIOLATIONS =true
EMAILREPORTLEVEL =3
REPORTLEVEL   =3
MAILMETHOD    =SENDMAIL
SYSLOGREPORTING =false
MAILPROGRAM   =/usr/sbin/sendmail -oi -t
```

**\[선택사항 - shell 스크립트용 코드\]** : 나중에 전체의 설치과정을 쉘 스크립트로 빼두고 실행하는 경우에 필요합니다. 우선은 필요가 없으니 넘어가도록 합니다. 경로의 표기법은 '/' 쓰기 전 아래와 같이 '\' 를 붙여주셔야 합니다.  
예\) /usr/helloman/report/ -&gt; \/usr\/helloman\/report\/

```text
# cat [Install folder path]/etc/twcfg.txt | sed 's/REPORTFILE[ ]*[=/a-zA-Z]*/REPORTFILE    =[Install folder path]/g' >> [Install folder path]/etc/twcfg.txt
```

수정된 twcfg.txt 파일을 기반으로 tw.cfg 파일을 생성합니다

```text
# [Install folder path]/sbin/twadmin --create-cfgfile -S [Install folder path]/etc/site.key [Install folder path]/etc/twcfg.txt
```

## 6. Rule 생성하기

twpol.txt 파일을 백업 해 둡니다.

```scheme
# cp [Install folder path]/etc/twpol.txt [Install folder path]/etc/twpol.txt.back
```

twpol.txt 파일에 사용할 전역변수 및 Rule 을 입력합니다.

```text
# vi [Install folder path]/etc/twpol.txt
```

전역으로 사용할 변수를 설정합니다. TWREPORT 는 twcfg.txt 에서 변경한 경로와 동일하게 지정해 줍니다.  
@@section GLOBAL 하단에 **\[전역변수명\] = "값";** 의 형태로 넣어주시면 Rule 을 생성하는 경우에 불러다가 사용하실 수 있습니다.

```bash
# Global Variable Definitions
@@section GLOBAL

TWROOT   = "[Install folder path]/sbin";
TWBIN    = "[Install folder path]/sbin";
TWPOL    = "[Install folder path]/etc";
TWDB     = "[Install folder path]/lib/tripwire/azvdi3.twd";
TWSKEY   = "[Install folder path]/etc";
TWLKEY   = "[Install folder path]/etc";

# 위에서 지정한 경로로 변경
TWREPORT = "[Report folder path]";      
```



### 6.1 파일 및 폴더 구분속성

| No | Attribute | Value | Description |
| :---: | :---: | :---: | :--- |
| 1 | file or folder | SEC\_CRIT | 변경할 수 없는 중요 파일 |
| 2 | file or folder | SEC\_SUID | SUID 또는 SGID 플래그가 설정된 바이너리 파일 |
| 3 | file or folder | SEC\_BIN | 변경할 수 없는 바이너리 파일 |
| 4 | file or folder | SEC\_CONFIG | 자주 변경되지는 않지만 자주 접근하는 설정파일 |
| 5 | file or folder | SEC\_LOG | 파일은 점점 커지고, 변경되지는 않는 로그파일 |
| 6 | file or folder | SEC\_INVARIANT | 절대 권한을 변경하면 안되는 폴더 |

```bash
# Global Variable Definitions
@@section GLOBAL

TWROOT   = "[Install folder path]/sbin";
TWBIN    = "[Install folder path]/sbin";
TWPOL    = "[Install folder path]/etc";
TWDB     = "[Install folder path]/lib/tripwire/azvdi3.twd";
TWSKEY   = "[Install folder path]/etc";
TWLKEY   = "[Install folder path]/etc";

# 위에서 지정한 경로로 변경
TWREPORT = "[Report folder path]";


@@section FS

SEC_CRIT      = $(SEC_IGNORE_NONE)-SHa ; 
SEC_SUID      = $(SEC_IGNORE_NONE)-SHa ; 
SEC_BIN       = $(SEC_READONLY) ;        
SEC_CONFIG    = $(SEC_DYNAMIC) ;         
SEC_TTY       = $(SEC_DYNAMIC)-ugp ;     
SEC_LOG       = $(SEC_GROWING) ;         
SEC_INVARIANT = $(SEC_TEMPORARY) ;       
SIG_LOW       = 33 ;
SIG_MED       = 66 ;
SIG_HI        = 100 ;      
```



### 6.2 Rule 생성 형식

**@@section FS** 를 입력한 후 그 아래에 Rule을 원하는 만큼 추가할 수 있습니다.

| No | Attribute | Value | Description |
| :---: | :---: | :---: | :--- |
| 1 | rulename | "Rule Name" | Rule 의 이름 |
| 2 | severity | SIG\_HI | 상당한 취약점을 가지는 중요한 파일 |
| 3 | severity | SIG\_MED | 보안이 중요한 중요하지 않은 파일 |
| 4 | severity | SIG\_LOG | 보안에 미치는 영향이 가장 적은 중요하지 않은 파일 |

```bash
# Global Variable Definitions
@@section GLOBAL

TWROOT   = "[Install folder path]/sbin";
TWBIN    = "[Install folder path]/sbin";
TWPOL    = "[Install folder path]/etc";
TWDB     = "[Install folder path]/lib/tripwire/azvdi3.twd";
TWSKEY   = "[Install folder path]/etc";
TWLKEY   = "[Install folder path]/etc";

# 위에서 지정한 경로로 변경
TWREPORT = "[Report folder path]";


@@section FS

SEC_CRIT      = $(SEC_IGNORE_NONE)-SHa ; 
SEC_SUID      = $(SEC_IGNORE_NONE)-SHa ; 
SEC_BIN       = $(SEC_READONLY) ;        
SEC_CONFIG    = $(SEC_DYNAMIC) ;         
SEC_TTY       = $(SEC_DYNAMIC)-ugp ;     
SEC_LOG       = $(SEC_GROWING) ;         
SEC_INVARIANT = $(SEC_TEMPORARY) ;       
SIG_LOW       = 33 ;
SIG_MED       = 66 ;
SIG_HI        = 100 ;

# My Rule
(
    rulename = "My Rule",
    severity = $(SIG_HI),
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

## 7. 데이터베이스 초기화

전역변수와 Rule 을 추가하였다면, 이제 twcfg.txt 파일을 반영해야 합니다.  
twadmin 명령을 통해서 tw.cfg 파일을 생성해 줍니다.

```css
# cd [Install folder path]/sbin
# ./twadmin --create-polfile -S [Install folder path]/site.key [Install folder path]/etc/tripwire/twpol.txt
```

위에서 생성한 site 비밀번호를 입력한 후, Enter 키를 눌러줍니다.

```text
Please enter your site passphrase:
Wrote configuration file: [Install folder path]/etc/tw.cfg
```

그 후, 데이터베이스를 초기화합니다.

```css
# ./tripwire --init
```

local 비밀번호로 설정할 문자열을 입력한 후, Enter 키를 눌러줍니다.

```text
Please enter your local passphrase:
```

데이터베이스 파일이 생기고, 초기화가 완료되었다는 메시지를 확인하실 수 있습니다.  
The database was successfully generated.

```text
Parsing policy file: [Install folder path]/etc/tw.pol
Generating the database...
*** Processing Unix File System ***
The object: "/run" is on a different file system...ignoring.
The object: "/sys" is on a different file system...ignoring.
The object: "/dev/hugepages" is on a different file system...ignoring.
The object: "/dev/mqueue" is on a different file system...ignoring.
Wrote database file: [Install folder path]/lib/tripwire/localhost.localdomain.twd
The database was successfully generated.
```

## 8. 시스템 체크 및 레포트 확인

tripwire --check 명령어를 사용하여 시스템을 체크합니다.

```text
# cd [Install folder path]/sbin
# ./tripwire --check
```

TWREPORT 경로에 들어가서 레포트 파일이 생겼는지 확인합니다.

```text
# cd [Report folder path]
# ls
```

저장된 레포트 파일을 읽어옵니다.

```text
# [Install folder path]/sbin/twprint -m r --twrfile [Report folder path]/*.twr
```

아래와 같은 형태의 레포트의 결과를 확인할 수 있습니다.

```text
Note: Report is not encrypted.
Open Source Tripwire(R) 2.4.3.7 Integrity Check Report

Report generated by:          root
Report created on:            2020년 05월 21일 (목) 오후 03시 28분 36초
Database last updated on:     Never

===============================================================================
Report Summary:
===============================================================================

Host name:                    localhost.localdomain
Host IP address:              127.0.0.1
Host ID:                      None
Policy file used:             /usr/local/etc/tw.pol
Configuration file used:      /usr/local/etc/tw.cfg
Database file used:           /usr/local/lib/tripwire/localhost.localdomain.twd
Command line used:            /usr/local/sbin/tripwire --check

===============================================================================
Rule Summary:
===============================================================================

-------------------------------------------------------------------------------
  Section: Unix File System
-------------------------------------------------------------------------------

  Rule Name                       Severity Level    Added    Removed  Modified
  ---------                       --------------    -----    -------  --------
  Tripwire Binaries               0                 0        0        0
* Tripwire Data Files             0                 4        0        2

Total objects scanned:  15
Total violations found:  6

===============================================================================
Object Detail:
===============================================================================

-------------------------------------------------------------------------------
  Section: Unix File System
-------------------------------------------------------------------------------

-------------------------------------------------------------------------------
Rule Name: Tripwire Data Files (/usr/local/lib/tripwire)
Severity Level: 0
-------------------------------------------------------------------------------
  ----------------------------------------
  Added Objects: 4
  ----------------------------------------

Added object name:  /usr/local/lib/tripwire/report/localhost.localdomain-20200521-152210.twr
Added object name:  /usr/local/lib/tripwire/report/localhost.localdomain-20200521-152216.twr
Added object name:  /usr/local/lib/tripwire/report/localhost.localdomain-20200521-152123.twr
Added object name:  /usr/local/lib/tripwire/localhost.localdomain.twd

-------------------------------------------------------------------------------
Rule Name: Tripwire Data Files (/usr/local/etc/tw.pol)
Severity Level: 0
-------------------------------------------------------------------------------
  ----------------------------------------
  Modified Objects: 1
  ----------------------------------------

Modified object name:  /usr/local/etc/tw.pol

  Property:            Expected                    Observed
  -------------        -----------                 -----------
* Modify Time          2020년 05월 21일 (목) 오후 03시 18분 58초
                                                   2020년 05월 21일 (목) 오후 03시 23분 55초
* CRC32                DTYVdE                      CyiaYH
* MD5                  AaZCLpcQ17bWFRPgtg4SHc      A6jMZKOAan5Tr1uypy18Kr



-------------------------------------------------------------------------------
Rule Name: Tripwire Data Files (/usr/local/etc/tw.cfg)
Severity Level: 0
-------------------------------------------------------------------------------
  ----------------------------------------
  Modified Objects: 1
  ----------------------------------------

Modified object name:  /usr/local/etc/tw.cfg

  Property:            Expected                    Observed
  -------------        -----------                 -----------
* Mode                 -rw-r-----                  -rw-r--r--
* Modify Time          2020년 05월 21일 (목) 오후 02시 45분 34초
                                                   2020년 05월 21일 (목) 오후 03시 27분 41초
* CRC32                A6vKsA                      CUkup3
* MD5                  AWqk3emnnxcVsmdzcZcrRH      D6MqZBwHaX4n7kGdh4d2p0



===============================================================================
Error Report:
===============================================================================

No Errors

-------------------------------------------------------------------------------
*** End of report ***

Open Source Tripwire 2.4 Portions copyright 2000-2018 Tripwire, Inc.  Tripwire is a registered
trademark of Tripwire, Inc. This software comes with ABSOLUTELY NO WARRANTY;
for details use --version. This is free software which may be redistributed
or modified only under certain conditions; see COPYING for details.
All rights reserved.
```



