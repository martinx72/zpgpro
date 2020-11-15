
## Before starting to build u-boot and kernel

**1) install packages you would need for building what we need.**

    sudo apt-get update
    sudo apt-get install -y git lzop build-essential gcc bc libncurses5-dev libc6-i386 lib32stdc++6 zlib1g:i386

**2) get proper toolchain for building**

    sudo mkdir -p /opt/toolchains
    wget https://releases.linaro.org/components/toolchain/binaries/6.3-2017.05/aarch64-linux-gnu/gcc-linaro-6.3.1-2017.05-x86_64_aarch64-linux-gnu.tar.xz
    sudo tar Jxvf gcc-linaro-6.3.1-2017.05-x86_64_aarch64-linux-gnu.tar.xz -C /opt/toolchains/

**3) set export variables properly**

    export ARCH=arm64
    export CROSS_COMPILE=aarch64-linux-gnu-
    export PATH=/opt/toolchains/gcc-linaro-6.3.1-2017.05-x86_64_aarch64-linux-gnu/bin/:$PATH


## Building u-boot for ZPG-Pro

    cd u-boot 
    ./make.sh odroidgo2
    cd sd_fuse
    ./sd_fusing.sh <device/path/of/your/card>



## Building Kernel for ZPG-Pro

    cd kernel
    make marsboard_defconfig
    make

**kernel image**: arch/arm64/boot/Image<br>
**kernel dtb**: arch/arm64/boot/dts/rockchip/rk3326-marsboard-linux.dtb

