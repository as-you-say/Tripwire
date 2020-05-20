# Install

## 1. Download & Unzip

Unzip tripwire-open-source-2.4.3.7.tar.gz

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

```

## 6. Generate Database

```text
cd [Install folder path]/sbin
./tripwire --init
```

## 7. Check

```text
cd [Install folder path]/sbin
./tripwire --check
```

