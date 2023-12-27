
# OpenBmc WebUI 環境設置

## 如何 build OpenBmc 在 ubuntu 64 20.04 上

參照 [官方 OpenBmc 文件](https://github.com/openbmc/openbmc)
 
 1. 安裝有關套件，以 ubuntu 為例
 ```
 sudo apt install git python3-distutils gcc g++ make file wget \
    gawk diffstat bzip2 cpio chrpath zstd lz4 bzip2
 ```

 2. clone OpenBmc code, 到 code 位置 setup

 ```
 git clone https://github.com/openbmc/openbmc
 cd openbmc
 . setup romulus //還有其他相關的環境可供部署
 ```

 3. build

 `bitbake obmc-phosphor-image`

 4. QEMU running up，下載 qemu 進行安裝
   參照 [OpenBmc develop 環境設置](https://github.com/openbmc/docs/blob/master/development/dev-environment.md)

  ```
  wget https://jenkins.openbmc.org/job/latest-qemu-x86/lastSuccessfulBuild/artifact/qemu/build/qemu-system-arm
  chmod u+x qemu-system-arm
  ```

 5. image 移到想要位置，對 image 進行 qemu 模擬

 ```
 cp ./tmp/deploy/images/romulus/obmc-phosphor-image-romulus.static.mtd ./

 qemu-system-arm -m 256 -M romulus-bmc -nographic -drive file=./obmc-phosphor-image-romulus.static.mtd,format=raw,if=mtd -net nic -net user,hostfwd=tcp::2222-:22,hostfwd=tcp::2443-:443,hostname=qemu
 ```
 > Note: 依照 REST, SSH 和 IPMI 在自己的 QEMU session，必須分別把 REST, SSH 和 IPMI 作 port forwarding

 ## 如何在 ubuntu 進行 web-ui 開發

 1. clone web-ui vue

 ```
 https://github.com/openbmc/webui-vue.git
 ```

 2. 依照 `npm install` 結束後， `npm run serve`

 3. 透過 vscode ssh 至 ubuntu 64 arm 進行開發