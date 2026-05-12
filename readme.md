#Tuxing Linux

This is the Tuxing Linux distribution's manual *Features:

-Lightweight

-Uses Musl Libc

-Busybox-based rootfs

-Designed for low-end hardware

-QEMU testable

*FAQ:

*What's Tuxing Linux?: Tuxing Linux is a Linux distro that aims to support legacy hardware and still being a leading-edge distro, providing a good user-experience and supporting as old computers as new and powerful computers;

*How light is it?: I did a lot of tests in QEMU and in this version without a graphical Interface, it consumes 20-25 mb ram(with 70mb allocated);

*What LIBC it uses?: The Tuxing Linux distro uses the musl libc, which provides good performance at low-end devices;

*How did you mount the rootfs: I constructed the rootfs with busybox binaries compiled static, it's a lightweight choice and can run all binaries in just one.(OBS: It runs ASH instead of BASH);

*Will you update this distro?and how it will be?:Yes, I will update this distro as soon as I can, and i will put a graphical lightweight interface(like some WM or DE) with a X server.

*Why can't you resolve all now?: To clarify I am a 14/15 years old boy that has a busy schedule (like school, this distro, music and other things). I'm making this distro because I really like linux and the idea of making something open-source that anyone could use.

*Have you changed the name of the distro?: Yes i had because, the preview name was being used in a Youtube Channel.
Here I'll show how to compile the system and provide the source code:

*Source code that I had to compile/use:

Kernel 6.19-5:https://cdn.kernel.org/pub/linux/kernel/v6.x/linux-6.19.5.tar.xz (the kernel used in Tuxing Linux)

Busybox:https://www.busybox.net/downloads/busybox-1.36.1.tar.bz2 (provide the binaries in the rootfs)

Musl:https://musl.libc.org/releases/musl-1.2.6.tar.gz (lightweight libc)

*Dependencies(need for compile): (build-essential/base-devel/"Development Tools" include gcc,make, binutils and other essential compilation tools)

Ubuntu/Debian: sudo apt install build-essential libelf-dev libncurses-dev cpio gzip

Fedora/RedHat: sudo dnf groupinstall "Development Tools" sudo dnf install libelf-devel ncurses-devel cpio gzip

Arch Linux: sudo pacman -S base-devel elfutils ncurses cpio gzip

*TUXING LINUX .config: I provided that in the project page in github in releases.

FOR TESTING!

-QEMU(if you want to test this virtually): Fedora/RedHat: sudo dnf install qemu-system-x86

Ubuntu/Debian: sudo apt install qemu-system-x86

Arch: sudo pacman -S qemu-system-x86

-Initramfs.cpio.gz(if you want to test virtually): it is basically the '/rootfs' folder compressed if you want to test in qemu

[AFTER DOWNLOADING ALL ABOVE] You have to go to the folder that you downloaded all(like: distro-downloads) and extract the kernel image:

cd /home/linux/distro-downloads tar -xf linux-6.19.5.tar.xz

After this you copy my .config:

cp .config linux-6.19.5/ cd linux-6.19.5

Now you compile the kernel:

make -j$(nproc) bzImage

After that you can go to the original folder:

cd /home/linux/distro-downloads

And run this command in terminal:

qemu-system-x86_64 -kernel /home/linux/distro-downloads/linux-6.19.5/arch/x86_64/boot/bzImage -initrd ~/distro-downloads/initramfs.cpio.gz -append "console=tty0 init=/init"

Congratulations! Now you are testing the Tuxing Linux distro

(Optional):

If you want to extract and get my rootfs you just need to extract the initramfs.cpio.gz using this command:

gunzip -c /home/linux/distro-downloads/initramfs.cpio.gz | cpio -idmv

So this was some steps to you build my system using the files that i have provided in GitHub to get the same result in less time but if you want to do it more manual just following the steps that i did to make my rootfs you can:

sudo mkdir -p /home/linux/distro-downloads/rootfs

cd /home/linux/distro-downloads/rootfs

sudo mkdir bin usr var etc sbin proc dev lib sys

After this you already have the same structure of the rootfs that i have made. Now if you want you can extract my initramfs.cpio.gz and copy the binaries or you can download and compile by your own and change what you want. Be free to do what you want to do, this project is aiming to help.

If someone can contribute to this project would help a lot I would really appreciate. Sorry for being so tiny this is just the 0.1 version and i'll improve up and add graphical things. -Ricardo Otávio Mariano da Silva [07/05/2026]
