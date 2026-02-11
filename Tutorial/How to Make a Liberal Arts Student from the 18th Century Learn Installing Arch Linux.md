> 
> 前提：笔者是一个来自十八世纪的文科生 $^{[1]}$，怎么学会装 Arch Linux?  
> 

进行粗略阅读 Arch Wiki，发现读懂需要 DFS 式阅读，递归深度达到 $O(1)$ 层，甚至有可能出现环，目前认为通读**较为困难**。  
电脑上装着 Windows + Arch (Hyprland (illogical-impulse) / Niri (Noctalia)) + Ubuntu (gnome)，由于 Windows 是屎，Ubuntu 是大恶霸，所以决定学习自己装 Arch。
此外，还有一个冷知识是，电脑上除了 Windows 其他系统都是 Pulsar 或 Qaaxaap 帮忙装的（拜谢！拜谢！）。 
为了迅速与现代接轨，在 Qaaxaap 的辅助下进行通读 Pulsar 的教程 [ArchLinux 简明安装&使用指南](https://www.luogu.com.cn/article/06our748) 后在移动硬盘上成功安装 Arch with Hyprland。  
然而对于我这种脑子并不好用的十八世纪文科生来说，想要完全理解全部安装步骤的核心与内涵或许需要大量时间，于是本文应运而生。  
本质是一篇没有含金量的速成式快餐教程，方便背诵。  
毕竟装 Arch 总比 OI 简单吧。嗯。
## Βήματα $\delta$: 制作 Ventoy 盘

## Βήματα $\varepsilon$: 磁盘分区
注意，这一步只是教你如何给磁盘分区，如果你会请跳过这一步。
### 对于 Windows 系统
右键任务栏 Windows 图标，在弹出的菜单里点“磁盘管理”那一项。  
会弹出一个窗口。在窗口的下半部分，你会找到一行或若干行。  
通常来说，那个叫作 “磁盘 0” 的那一行是你的电脑的磁盘。  
如果你插着 U 盘或者移动硬盘的话，那么下面或许还有若干行叫作“磁盘 1”“磁盘 2”，以此类推，它们代表着你的 U 盘或移动硬盘。  
每一行里面你会看见若干的大小不一的块，这些块就是磁盘的**分区**。  
注意，你的电脑里是一块完整的磁盘，尽管你在表面上看似乎电脑上有“C 盘”“D 盘”等等，但其实它们都只是那块完整的磁盘的不同分区罢了，你可以注意到你的电脑上的磁盘可能还有别的没名字的分区，它们也各有所用，只是你平时看不到罢了。
分区之间是可以分裂、合并的。  
在窗口的上半部分，你会看到各个分区的详细信息。

你要在窗口的**下半**部分选择一个分区（也就是一个“块”状物），这个分区在你的电脑上，或者是在你的盘上。  
右键你选择的分区，点“压缩卷”，在弹出的窗口中，你会先看到一个“查询压缩空间”的窗口，等待片刻则会看到一个“压缩”的窗口。你会发现其中有一栏叫作“输入压缩空间量”可以输入，输入的数单位为 $\mathrm{MiB}^{[3]}$, 其中 $1024\mathrm{MiB}=1\mathrm{GiB}$。然后点击压缩。  

压缩后你将看到一块空分区。

### 对于 Linux 系统
电脑开机前把你的 Ventoy 盘插进去，点开机键之后猛按 `F12`, 会进一个界面，进去之后选择你的盘的名字（一般叫 `USB Device xxx……`），就可以进入 Ventoy 界面。  
选择 Gparted Live，进去之后啥也不要管，遇到**选项**就直接无脑按 `Enter`。  

直到进到一个长得比较神秘的桌面里面。
会弹出一个窗口。在窗口的上半部分，你会找到一行。  
一行里面你会看见若干的大小不一的块，这些块就是磁盘的**分区**。  
你可以看到，这些磁盘名字都叫 `/dev/nvme*n*p*`，这就代表着你的电脑上的系统盘。  
如果你插 U 盘或移动硬盘的话，你可以点击窗口的右上角，会发现还有一个 `/dev/sd*`，那个 `*` 是某个字母，你可以点一下它，然后就会切到你的 U 盘或移动硬盘。
你要在窗口的**下半**部分选择一个分区（也就是一个“块”状物），这个分区在你的电脑上，或者是在你的盘上。  
右键窗口下半部分你选择的分区，点“Resize”，在弹出的窗口中，你会先看到一个“查询压缩空间”的窗口，等待片刻则会看到一个“压缩”的窗口。你会发现其中有一栏叫作“输入压缩空间量”可以输入，输入的数单位为 $\mathrm{MiB}^{[3]}$, 其中 $1024\mathrm{MiB}=1\mathrm{GiB}$。然后点击压缩。  


现在，你要选择你是要在电脑上装 Arch 还是在盘上装 Arch。  
在电脑上就代表着你的电脑会变成**双系统**，在盘上装代表着你以后如果想要启动 Arch 需要在开机之前插上盘，然后从盘上启动。  
是的，在盘上装意味着，你的 U 盘或移动硬盘将会成为你真正的电脑 $^{[2]}$。等价的表述是，你将不用再携带一个大体积的电脑，只需要带一个盘，到有设备的地方，就可以**随时启动你的电脑**。

## Βήματα 1: 安装之前 
在 Linux 命令行中：  
`cd <目录>` 用于将目前命令行所在的位置跳转到你输入的目录的位置。目录其实就是文件夹所在的路径。注意尖括号只是为了说明这是一个依实际情况而定的某种可变项，不代表在实际输入中真的有这个尖括号。 
`vim <文件>` 用 vim 在命令行中打开文件，vim 是一种代码编辑器。事实上，对于任何代码编辑器都是同理，比如说 `code <文件>` 就是用 Visual Studio Code 打开文件，`emacs <文件>` 就是用 Emacs 打开文件。如果文件不存在，就会建立一个空文件并用你所选的编辑器打开。  
`touch <文件>` 是在目前所在目录新建一个某文件但不打开。  
命令前面加 `sudo` 代表以管理员权限运行，可以干一些更深层的东西。  
`su` 代表着后面的所有命令都将以 `sudo` 权限运行。  
命令行中复制粘贴是 `Ctrl+Shift+c/v`, 不是 `Ctrl+c/v`。  
`Ctrl+c` 在命令行中代表着强制中断现在运行的命令的运行。
你大概知道这些就差不多了吧。后文中看不懂的可以不用管或自行查阅。毕竟本文只是为了速装以及背诵。  

特别地，在 Arch Linux 中：  
pacman 是官方**软件包管理器**，yay/paru 是 AUR 中的软件包管理器，其实就是非官方的。  
软件包其实就是安装应用程序用的，Arch Linux 中所有软件都靠软件包安装，没有显式的图形化安装。简洁地说，就是仅仅靠命令行安装程序。这意味着你将不需要去任何软件的官网去自己下载，也不需要考虑软件装在哪里，仅仅需要联网然后在命令行里输入命令就可以安装程序。使得各种软件的管理比 Windows 要方便许多。  
`sudo pacman -S <软件包名>` 以及 `sudo yay -S <软件包名>` 用来安装软件包。pacman 其实是 yay 的子集，所以理论上来说你只需要用 yay 就可以了。  
`yay <软件包名>` 用来查找该软件包，找到之后你可以直接选择安装哪个。  
`sudo pacman -R <软件包名>` 以及 `sudo yay -R <软件包名>` 用来删除软件包。   
注意，最好不要用 `sudo` 权限来运行 `yay ...`，然而 `pacman ...` 必须需要 `sudo` 权限。 

你需要掌握一些基本的 Vim 使用技巧：
进入 Vim 编辑器后，按 `i` 进入插入模式，进入插入模式之后你便可以随意进行输入与删除，按 `esc` 退出插入模式。输入 `:wq` 并回车代表保存并退出 Vim，`:q!` 并回车代表强制退出不保存。按 `V` 进入拖选模式，按 `gg` 光标到文章首，按 `G` 光标到文章末，按 `x` 删除字符并存入剪贴板，按 `y` 复制选中的内容，按 `p` 粘贴剪贴板中的内容，按 `u` 回退到上一步操作之前。`h,j,k,l` 分别代表光标向左、下、上、右移动一格。当然你也可以使用传统方法的方向键进行这一步。    
根据此，我们得知，**将文章内容全部删除的命令是 `ggVGx`**。（你猜我为什么加粗这句）  

以及一些更根本的东西：
1. `/` 是 Linux 系统的根目录，一切文件都在其中
2. `~` 是 Linux 系统的主文件夹，你的文档，下载内容，图片，桌面等等都在其中。
3. Linux 的文件路径格式是 `/.../.../.../...`，比如说 `~` 的本质其实是 `/home/<username>/`。
4. Linux 是一类操作系统的总称，Arch Linux 是 Linux 的一种。

以及最重要的一点：
1. **Windows 是屎！**

我想到的你**最起码**要知道的就这些了。  

## Βήματα 2: 安装时
将你的 Ventoy 盘插上，然后开机过程中狂按 `F12`，进去之后选择形如 `archlinux******.iso` 可以调出 Arch Linux 安装程序。  
进去之后默认选项不要动直接回车。    
过一会你会看到一个 Welcome to Archlinux！的字样。  
然后输入以下命令：

```bash
systemctl stop reflector.service  
```

如果使用无线网络则进入下一步。  

```bash
iwctl # 进入交互式命令行 
device list # 列出无线网卡设备名，比如无线网卡可能叫 wlan0 
station <无线网卡设备名> scan # 扫描网络 
station <无线网卡设备名> get-networks # 列出所有 wifi 网络 
station <无线网卡设备名> connect <wifi-name>

# 输入 Wifi 密码，那种需要网站上登录的 WiFi 是不行的，注意它并不会提醒你密码错误  
# 输入后离开
exit
```

现在连上网了。

```bash
timedatectl set-ntp true 
timedatectl status          
vim /etc/pacman.d/mirrorlist

# 进入后清空全部（ggVGx）并进入插入模式（i），输入
Server = https://mirrors.ustc.edu.cn/archlinux/$repo/os/$arch
# 保存并离开 vim  
```

输入 `lsblk` 查看磁盘情况，找到你要装 Arch 的磁盘的名字，我们把它记作 `<disk>`。  
这个名字或许是 `sd*,nvme*n*p`, 注意，这是磁盘名，不是分区名，它的最后一位不是数字而是字母。  

```bash
cfdisk /dev/<disk>
# 进入 cfdisk，注意你现在用方向键以及回车键来进行选择  

# 注意，你也可以在装 Arch 之前提前分好三个 2GB，16GB，若干GB 的分区，如果提前分好了的话就不需要执行接下来的三个 New 【请参考 Βήματα ε】 
# 注意每次 New 的时候选中的都是 Free Space
[New] 
2GB  
# 回车
[New]
16GB 
# 回车
[New]
# 回车


# 对于 2GB 的分区
[Type]
[EFI System]

# 对于 16GB 的分区
[Type]
[Linux Swap]

# 对于最后一个剩下的大分区
[Type]
[Linux Filesystem]


[Write]
yes
[Quit]
```

现在你应该已经成功分好区了！
运行 `lsblk` 复查，并记住你的三个分区的名字（注意这次是分区名），按照大小从小到大记作 `<efi>,<swap>,<main>`。  

继续。
```bash
mkswap /dev/<swap>  
swapon /dev/<swap>  
# mkfs.vfat /dev/<efi> # 注意虚拟机或者没装过系统的实体机上才运行这个！！
mkfs.btrfs -L <卷标> /dev/<swap> # <卷标> 是自定义名称，就用英文，大小写随便，不要有特殊字符比如说空格
btrfs subvolume create /mnt/@
btrfs subvolume create /mnt/@home
mount -t btrfs -o subvol=/@,compress=zstd /dev/<main> /mnt           
mkdir /mnt/home                                                         
mount -t btrfs -o subvol=/@home,compress=zstd /dev/<main> /mnt/home  
mkdir /mnt/boot
mount /dev/<main> /mnt/boot                                                  
mkdir /mnt/etc
touch /mnt/etc/vconsole.conf       
pacstrap /mnt base base-devel linux linux-firmware btrfs-progs networkmanager vim sudo zsh zsh-completions
genfstab -U /mnt > /mnt/etc/fstab
arch-chroot /mnt
vim /etc/hostname
# 按 i 进入插入模式，输入主机名，依然是英文，不要有特殊字符
<Name>
# :wq 退出
vim /etc/hosts
# 在最后一行添加
127.0.1.1    Arch.localdomain Arch
# :wq 退出
ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
hwclock --systohc
vim /etc/locale.gen 
# 将以下两项取消注释（也就是删掉这两项开头的 #） 
en_US.UTF-8 UTF-8
zh_CN.UTF-8 UTF-8 (root)$ locale-gen
# :wq 退出
locale-gen
passwd root
# 设个密码，不限制强度
pacman -S intel-ucode grub efibootmgr os-prober
grub-install --target=x86_64-efi --efi-directory=/boot --bootloader-id=<Name>
vim /etc/default/grub
# 把前面的这一句中的 "loglevel=3,quiet" 改成 "loglevel=5"
GRUB_CMDLINE_LINUX_DEFAULT="loglevel=5"
# 翻到最后，把这一句取消注释，也就是将 # 删掉
GRUB_DISABLE_OS_PROBER=false
# 按 :wq 退出
grub-mkconfig -o /boot/grub/grub.cfg
```

到这里你算是装好 Arch 了。  
## Βήματα 3: 安装完成
接下来，我们将要离开安装程序，进入 Arch Linux 系统。


___
**【附录】**
$[1]$：这是笔者由于对于计算机科学认知水平以及电脑应用能力远低于同机房两位该领域顶尖水平大神而自嘲的说法。不过或许总比「试图在 Linux 上直接运行 `.exe` 文件」的 xxx、「不会开 `Run in Terminal` 而只能使用 CPH」的 xx，以及「大抵不知道什么是 Linux」「认为会 `sudo apt update` 很牛」的部分选手要稍微强一点的吧……尽管如此，笔者在 Arch 用户中应当处于倒序 1% 水平。
$[2]$：
$[3]$：尽管显示的单位是 $\mathrm{MB}$，但 $\mathrm{MB}$ 是 $1000$ 进制的，实际的单位是 $1024$ 进制的 $\mathrm{MiB}$。
