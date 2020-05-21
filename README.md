# Install

## 1. Download & Unzip

```
# wget https://github.com/Tripwire/tripwire-open-source/releases/download/2.4.3.7/tripwire-open-source-2.4.3.7.tar.gz
# tar -zxvf tripwire-open-source-2.4.3.7.tar.gz
# cd ./tripwire-open-source-2.4.3.7
```

## 2. Install gcc, gcc-c++ package

```text
# yum -y install gcc gcc-c++
```

## 3. Set Install folder path

```text
# ./configure --prefix=[Install folder path]
```

## 4. Compile

```text
# make
# make install
```

## 5. Create Rule

```text
# vi [Install folder path]/etc/twpol.txt
```

### 5.1 Common Attribute

| No | Attribute | Value | Description |
| :---: | :---: | :---: | :--- |
| 1 | file or folder | SEC\_CRIT | Critical files that cannot change |
| 2 | file or folder | SEC\_SUID | Binaries with the SUID or SGID flags set |
| 3 | file or folder | SEC\_BIN | Binaries that should not change |
| 4 | file or folder | SEC\_CONFIG | Config files that are changed infrequently but accessed often |
| 5 | file or folder | SEC\_LOG | Files that grow, but that should never change |
| 6 | file or folder | SEC\_INVARIANT | Directories that should never change permission |

```bash
# Global Variable Definitions
#@@section GLOBAL

TWROOT   = "[Install folder path]/sbin";
TWBIN    = "[Install folder path]/sbin";
TWPOL    = "[Install folder path]/etc";
TWDB     = "[Install folder path]/lib/tripwire/azvdi3.twd";
TWSKEY   = "[Install folder path]/etc";
TWLKEY   = "[Install folder path]/etc";
TWREPORT = "[Install folder path]/tripwire/report";

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



### 5.2 Custom Rule Format

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

## 6. Generate Database

```css
cd [Install folder path]/sbin
./twadmin -m P [Install folder path]/etc/twpol.txt
./tripwire --init
```

## 7. Check

```text
cd [Install folder path]/sbin
./tripwire --check
```

