# zimbra_ose_build

Zimbra Open Source Edition (OSE，開源版) 打包安裝檔，採用官方 zmbuild 套件庫打包而成，如只需取得二進位安裝檔，請至本專案 Release 直接下載取得。

---

# 環境準備

請依據要打包的目標安裝環境，分別安裝作業系統版本的必要套件，本專案以 Ubuntu 20.04、22.04 為打包目標。

Ubuntu 20.04
```
apt install software-properties-common openjdk-8-jdk \
  ant ant-optional ant-contrib ruby git maven build-essential \
  debhelper screen
```

Ubuntu 22.04
```
apt install \
  apt-utils ca-certificates tzdata curl wget \
  software-properties-common apt-transport-https \
  git perl ruby pkg-config \
  libidn11-dev libwww-perl libz-dev libaio-dev libncurses-dev libexpat1-dev \
  libpcre3-dev libperl-dev libpopt-dev libbz2-dev \
  libtest-simple-perl libsocket6-perl libtest-inter-perl libtest-warn-perl libtest-deep-perl \
  debhelper lib32z1-dev build-essential \
  openjdk-8-jdk ant ant-optional ant-contrib maven rsync \
  screen sudo
```

---

# 打包安裝檔

## Zimbra 9.0.0 Patch 44
```
cd /root
mkdir installer-build-p44
cd installer-build-p44

git clone --depth 1 --branch 9.0.0.p44 https://github.com/Zimbra/zm-build.git

cd zm-build

ENV_CACHE_CLEAR_FLAG=true \
./build.pl --ant-options -DskipTests=true \
  --git-default-tag=9.0.0.p44,9.0.0.p43,9.0.0.p42,9.0.0.p41,9.0.0.p40,9.0.0.p39,9.0.0.p38,9.0.0.p37,9.0.0.p36,9.0.0.p35,9.0.0.p34,9.0.0.p33,9.0.0.p32.1,9.0.0.p32,9.0.0.p31,9.0.0.p30,9.0.0.p29,9.0.0.p28,9.0.0.p27,9.0.0.p26,9.0.0.p25,9.0.0.p24.1,9.0.0.p24,9.0.0.p23,9.0.0.p22,9.0.0.p21,9.0.0.p20,9.0.0.p19,9.0.0.p18,9.0.0.p17,9.0.0.p16,9.0.0.p15,9.0.0.p14,9.0.0.p13,9.0.0.p12,9.0.0.p11,9.0.0.p10,9.0.0.p9,9.0.0.p8,9.0.0.p7,9.0.0.p6.1,9.0.0.p6,9.0.0.p5,9.0.0.p4,9.0.0.p3,9.0.0.p2,9.0.0.p1,9.0.0 \
  --build-release=KEPLER \
  --build-release-no=9.0.0 \
  --build-release-candidate=GA \
  --build-type=FOSS \
  --build-thirdparty-server=files.zimbra.com \
  --build-no=1044 \
  --no-interactive
```

## Zimbra 10.1.10
```
cd /root
mkdir installer-build-10110
cd installer-build-10110

git clone --depth 1 --branch 10.1.10 https://github.com/Zimbra/zm-build.git

cd zm-build

ENV_CACHE_CLEAR_FLAG=true ./build.pl \
    --ant-options "-DskipTests=true" \
    --git-default-tag=10.1.10,10.1.9,10.1.8,10.1.7,10.1.6,10.1.5,10.1.4,10.1.3,10.1.2,10.1.1,10.1.0,main \
    --build-release-no=10.1.10 \
    --build-type=FOSS \
    --build-no=10110 \
    --build-release=LIBERTY \
    --build-release-candidate=GA \
    --build-thirdparty-server=files.zimbra.com \
    --no-interactive
```
