# Padavan
基于hanwckf,chongshengB以及padavanonly的源码整合而来，支持7603/7615/7915的kvr  
编译方法同其他Padavan源码，主要特点如下：  
1.采用padavanonly源码的5.0.4.0无线驱动，支持kvr  
2.添加了chongshengB源码的所有插件  
3.其他部分等同于hanwckf的源码，有少量优化来自immortalwrt的padavan源码  
4.添加了MSG1500的7615版本config  
  
以下附上他们四位的源码地址供参考  
https://github.com/hanwckf/rt-n56u  
https://github.com/chongshengB/rt-n56u  
https://github.com/padavanonly/rt-n56u  
https://github.com/immortalwrt/padavan
  
最后编译出的固件对7612无线的支持已知是有问题的，包含7612的机型比如B70是无法正常工作的  
已测试的机型为MSG1500-7615，JCG-Q20，CR660x  
  
固件默认wifi名称
 - 2.4G：机器名_mac地址最后四位，如K2P_9981
 - 5G：机器名_5G_mac地址最后四位，如K2P_5G_9981

wifi密码
 - 1234567890

管理地址
 - 192.168.2.1

管理账号密码
 - admin
 - admin

**最近的更新代码都来自于hanwckf和MelsReallyBa大佬的4.4内核代码**
- https://github.com/hanwckf/padavan-4.4
- https://github.com/MeIsReallyBa/padavan-4.4





Welcome to the rt-n56u project

This project aims to improve the rt-n56u and other supported devices on the software part, allowing power user to take full control over their hardware. This project was created in hope to be useful, but comes without warranty or support. Installing it will probably void your warranty. Contributors of this project are not responsible for what happens next.

How do I get set up?
Get the tools to build the system or Download pre-built system image
Feed the device with the system image file (Follow instructions of updating your current system)
Perform factory reset
Open web browser on http://my.router to configure the services
Contribution guidelines
To be completed
特别说明
汉化字典来自：https://github.com/gorden5566/padavan
更新日志：https://www.jianshu.com/p/d76a63a12eae
固件特点
使用gorden5566的汉化字典
aria2前端更换为AriaNg
curl可选编译可执行程序 CONFIG_FIRMWARE_INCLUDE_CURL
使用了PROMETHEUS提供的部分补丁
使用了Linaro1985/padavan-ng的部分软件包
可选以下插件：
scutclient CONFIG_FIRMWARE_INCLUDE_SCUTCLIENT
gdut-drcom CONFIG_FIRMWARE_INCLUDE_GDUT_DRCOM
dogcom CONFIG_FIRMWARE_INCLUDE_DOGCOM
minieap CONFIG_FIRMWARE_INCLUDE_MINIEAP
njit-client CONFIG_FIRMWARE_INCLUDE_NJIT_CLIENT
napt66 CONFIG_FIRMWARE_INCLUDE_NAPT66
softether-vpnserver CONFIG_FIRMWARE_INCLUDE_SOFTETHERVPN_SERVER
softether-vpnclient CONFIG_FIRMWARE_INCLUDE_SOFTETHERVPN_CLIENT
softether-vpncmd CONFIG_FIRMWARE_INCLUDE_SOFTETHERVPN_CMD
vlmcsd CONFIG_FIRMWARE_INCLUDE_VLMCSD
ttyd CONFIG_FIRMWARE_INCLUDE_TTYD
lrzsz CONFIG_FIRMWARE_INCLUDE_LRZSZ
htop CONFIG_FIRMWARE_INCLUDE_HTOP
nano CONFIG_FIRMWARE_INCLUDE_NANO
iperf3 CONFIG_FIRMWARE_INCLUDE_IPERF3
dump1090 CONFIG_FIRMWARE_INCLUDE_DUMP1090
rtl-sdr CONFIG_FIRMWARE_INCLUDE_RTL_SDR
samba3.6 CONFIG_FIRMWARE_INCLUDE_SMBD36
mtr CONFIG_FIRMWARE_INCLUDE_MTR
socat CONFIG_FIRMWARE_INCLUDE_SOCAT
srelay CONFIG_FIRMWARE_INCLUDE_SRELAY
3proxy CONFIG_FIRMWARE_INCLUDE_3PROXY
mentohust CONFIG_FIRMWARE_INCLUDE_MENTOHUST
frpc CONFIG_FIRMWARE_INCLUDE_FRPC
frps CONFIG_FIRMWARE_INCLUDE_FRPS
tunsafe CONFIG_FIRMWARE_INCLUDE_TUNSAFE
wireguard-go CONFIG_FIRMWARE_INCLUDE_WIREGUARD
smartdns CONFIG_FIRMWARE_INCLUDE_SMARTDNS
已适配除官方适配外的以下机型
PSG1208
PSG1218
5K-W20 (USB)
OYE-001 (USB)
NEWIFI-MINI (USB)
MI-MINI (USB)
MI-3 (USB)
MI-3C
MI-4
MI-R3G (USB)
MI-R4A
MI-R3P (USB)
HC5661A
HC5761A (USB)
HC5861B
360P2 (USB)
MI-NANO
MZ-R13
MZ-R13P
RT-AC1200GU (USB)
XY-C1 (USB)
WR1200JS (USB)
NEWIFI3 (USB)
B70 (USB)
A3004NS (USB)
K2P
K2P-USB (USB)
JCG-836PRO (USB)
JCG-AC860M (USB)
DIR-882 (USB)
DIR-878
MR2600 (USB)
WDR7300
RM2100
CR660x (CR6606, CR6608, CR6609)
R2100
JCG-Y2 (USB)
E8820V2 (USB)
ZTE_E8820S (USB)
MSG1500 (USB)
R6220 (USB)
NETGEAR-CHJ (R6260, R6350, R6850, WAC124)
NETGEAR-BZV (R6800, R6700-v2, R7200, Nighthawk AC2400)
编译说明
安装依赖包
# Debian/Ubuntu
sudo apt update
sudo apt install unzip libtool-bin curl cmake gperf gawk flex bison nano xxd \
	fakeroot kmod cpio git python3-docutils gettext automake autopoint \
	texinfo build-essential help2man pkg-config zlib1g-dev libgmp3-dev \
	libmpc-dev libmpfr-dev libncurses5-dev libltdl-dev wget libc-dev-bin

# Archlinux/Manjaro
sudo pacman -Syu --needed git base-devel cmake gperf ncurses libmpc \
        gmp python-docutils vim rpcsvc-proto fakeroot cpio help2man

# Alpine
sudo apk add make gcc g++ cpio curl wget nano xxd kmod \
	pkgconfig rpcgen fakeroot ncurses bash patch \
	bsd-compat-headers python2 python3 zlib-dev \
	automake gettext gettext-dev autoconf bison \
	flex coreutils cmake git libtool gawk sudo

# CentOS 7
sudo yum update
sudo yum groupinstall "Development Tools"
sudo yum install ncurses-* flex byacc bison zlib-* texinfo gmp-* mpfr-* gettext \
	libtool* libmpc-* gettext-* python-docutils nano help2man fakeroot

# CentOS 8
sudo yum update
sudo yum groupinstall "Development Tools"
sudo yum install ncurses-* flex byacc bison zlib-* gmp-* mpfr-* gettext \
	libtool* libmpc-* gettext-* nano fakeroot

# CentOS 8不能直接通过yum安装texinfo，help2man，python-docutils。请去官网下载发行的安装包编译安装
# 以texinfo为例
# cd /usr/local/src
# sudo wget http://ftp.gnu.org/gnu/texinfo/texinfo-6.7.tar.gz
# sudo tar zxvf texinfo-6.7.tar.gz
# cd texinfo-6.7
# sudo ./configure
# sudo make
# sudo make install
克隆源码git clone --depth=1 https://github.com/Yutsuki92/vb1980-Padavan3.4.git /opt/rt-n56u
准备工具链
cd /opt/rt-n56u/toolchain-mipsel

# （推荐）使用脚本下载预编译的工具链：
sh dl_toolchain.sh

# 或者，也可以从源码编译工具链，这需要一些时间：
./clean_toolchain
./build_toolchain
(可选) 修改机型配置文件
nano /opt/rt-n56u/trunk/configs/templates/PSG1218.config
开始编译
cd /opt/rt-n56u/trunk
# 对于WSL环境，建议使用sudo进行编译，或者使用fakeroot-tcp代替fakeroot
fakeroot ./build_firmware_modify PSG1218
# 脚本第一个参数为路由型号，在trunk/configs/templates/中
# 编译好的固件在trunk/images里
# 首次编译完成后，如果需要再次编译其它固件，需要执行清理脚本：
./clear_tree
请参阅
https://www.jianshu.com/p/cb51fb0fb2ac
https://www.jianshu.com/p/6b8403cdea46

