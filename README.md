# zimbra-ose-build

Zimbra Open Source Edition (OSE，開源版) 打包安裝檔，採用官方 zm-build 套件庫打包而成。

如您只需取得二進位安裝檔進行使用，請您移駕至本專案 Release 處直接下載取得。

連結：https://github.com/jasoncheng7115/zimbra-ose-build/releases

> 由 Jason Cheng 個人打包，採用官方標準程序及乾淨 Ubuntu Server 環境作業。

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


---

## 免責聲明

本專案 (zimbra-ose-build) 是基於個人興趣與研究目的而進行，提供給社群使用。請注意：

- 本專案僅供學習、研究及個人使用，製作者不對本工具及打包成果的功能完整性、穩定性或適用性提供任何明示或暗示的保證。
- 本專案所打包之二進位安裝檔完全採用 Zimbra 官方 zm-build 工具打包而成，不含任何額外添加物。
- 製作者需自行承擔使用本專案的一切風險，包括但不限於資料遺失、系統損壞或其他可能發生的問題。
- 開發者不對因使用或無法使用本專案而導致的任何直接或間接損失負責，包括但不限於利潤損失、業務中斷或資料損失。
- 本專案提供所有二進位安裝檔與操作說明的目的是分享知識，使用者應在符合當地法律法規的前提下使用。
- 專案內容可能會不定期更新，製作者保留隨時修改或終止服務的權利，且無需事先通知。

使用本專案表示您已閱讀、理解並同意上述免責聲明的所有條款。如不同意，請勿使用本專案。

---
