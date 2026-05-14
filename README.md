# Linux-commands
Linux Terminal Commands for personal use 
Yess welcome to the “Linux commands that make you feel powerful” phase.

Here are actually useful beginner-safe Ubuntu commands you’ll probably use a LOT.

🧠 System Info

Show disk space

    df -h

Human-readable storage info.

⸻

Show RAM usage

    free -h

⸻

Show system info

    neofetch

Looks cool too 

Install first:

    sudo apt install neofetch

⸻

📦 Package Management

Update package lists

    sudo apt update

⸻

Upgrade installed packages

    sudo apt upgrade

⸻

Install apps

    sudo apt install vlc

Example installs VLC.

⸻

Remove apps

    sudo apt remove vlc

⸻

🧹 Cleanup

Clean package cache

    sudo apt clean

⸻

Remove unnecessary packages

    sudo apt autoremove

VERY useful.

⸻

📂 File Navigation

Show current folder

    pwd

⸻

List files

    ls

Better version:

    ls -lah

Shows hidden files + sizes.

⸻

Enter folder

    cd Downloads

⸻

Go back one folder

    cd ..

⸻

Go home instantly

    cd ~

⸻

🔥 Power Commands

Clear terminal screen

    clear

Or press:

    Ctrl + L

⸻

Open current folder in Files app

    nautilus .

That dot matters 

⸻

Shutdown PC

    sudo shutdown now

⸻

Restart PC

    sudo reboot

⸻

👀 Hidden Linux Tricks

Show command history

    history

⸻

Repeat previous command

    !!

Dangerous but cool 

⸻

Search previous commands

Press:

    Ctrl + R

Then type part of old command.

INSANELY useful later.

⸻

🧠 Useful Future Dev Commands

Git version

    git --version

⸻

Python version

    python3 --version

⸻

C compiler version

    gcc --version

⸻

🐧 Beginner Survival Tip

If a command scares you:

add:

    --help

Example:

  ls --help

Linux literally explains itself.

⸻

Most useful keyboard shortcuts 

Open terminal

    Ctrl + Alt + T

⸻

Interrupt running command

    Ctrl + C

LIFESAVER.

⸻

Auto-complete filenames

Press:

    Tab

This is Linux magic.


📍📍📍📍📍📍📍📍📍📍📍📍📍

Absolutely — here’s a long, practical cheatsheet of the commands and workflows we used across your Ubuntu + Kali journey. I’ve grouped them by task so it actually feels usable instead of just a random command dump.

⸻

Kali + Ubuntu Survival Cheatsheet

1) Basic Linux navigation

These are the “I am here, what am I looking at?” commands.

pwd

Shows your current directory.

ls

Lists files and folders in the current directory.

ls -lh

Lists files with human-readable sizes.

ls -la

Lists everything, including hidden files.

cd /path/to/folder

Moves into a folder.

cd ..

Moves one level up.

cd ~

Goes to your home folder.

cd /

Goes to the root of the filesystem.

⸻

2) File and folder work

mkdir myfolder

Creates a folder.

mkdir -p /mnt/persistence

Creates a folder and any missing parent folders too.

touch myfile.txt

Creates an empty file.

echo "hello" > myfile.txt

Writes text into a file.

cat myfile.txt

Shows file contents.

cp file1 file2

Copies a file.

mv oldname newname

Renames or moves a file.

rm file.txt

Deletes a file.

rm -r foldername

Deletes a folder and its contents.

⸻

3) System identity and user info

whoami

Shows the current username.

hostname

Shows the computer name.

uname -a

Shows kernel and system details.

date

Shows current date and time.

⸻

4) Disk and partition discovery

These were huge for your USB setup.

lsblk

Shows disks, partitions, and mount points.

fdisk -l

Shows detailed disk/partition layout.

sudo blkid

Shows filesystem labels and UUIDs.

df -h

Shows disk usage in human-readable form.

free -h

Shows RAM usage in human-readable form.

mount

Shows currently mounted filesystems.

mount | grep persistence

Filters mounted filesystems for persistence-related entries.

⸻

5) USB and partition setup

These are the commands that helped build the Kali persistence USB.

Format a partition as ext4 and label it persistence

sudo mkfs.ext4 -L persistence /dev/sda3

What it does:

* formats /dev/sda3 as ext4
* labels it persistence

Mount the partition

sudo mount /dev/sda3 /mnt/persistence

Check contents

ls /mnt/persistence

Create the persistence configuration file

echo "/ union" | sudo tee /mnt/persistence/persistence.conf

This is the magic line that tells Kali to use the partition as writable overlay storage.

Verify the file

cat /mnt/persistence/persistence.conf

Expected output:

/ union

Unmount safely

sudo umount /mnt/persistence

If you used a different mount point:

sudo umount /mnt

⸻

6) ISO flashing and USB writing

These are the low-level commands that wrote the Linux image to your USB.

Write an ISO directly to USB with dd

sudo dd if=~/Downloads/yourfile.iso of=/dev/sdX bs=4M

What each part means:

* if= input file
* of= output device
* bs=4M block size for speed

If your system supports it, you can add:

sudo dd if=~/Downloads/yourfile.iso of=/dev/sdX bs=4M status=progress

If status=progress gives trouble, just omit it.

Sync after writing

sync

This flushes writes before unplugging the USB.

⸻

7) Package management on Kali/Ubuntu

These are the everyday install/update commands.

Update package lists

sudo apt update

Upgrade installed packages

sudo apt upgrade -y

Update and upgrade together

sudo apt update && sudo apt upgrade -y

Install a package

sudo apt install package-name

Example:

sudo apt install htop

Install with automatic yes

sudo apt install htop -y

Remove unused packages

sudo apt autoremove -y

Clean downloaded package cache

sudo apt clean

⸻

8) Useful everyday packages

These are the ones we talked about as useful for your lab.

sudo apt install htop -y

Real-time process and RAM view.

sudo apt install wireshark -y

Packet analyzer.

sudo apt install nmap -y

Network scanner.

sudo apt install curl wget git -y

Download tools and Git support.

sudo apt install python3 python3-pip -y

Python environment.

sudo apt install net-tools iproute2 dnsutils -y

Useful networking utilities.

sudo apt install tcpdump tshark -y

Terminal packet capture tools.

sudo apt install firefox-esr -y

Stable Firefox version for Kali.

sudo apt install chromium

Chromium browser.

⸻

9) Real-time RAM and process monitoring

Best one

htop

Interactive process monitor, real-time RAM/CPU view.

Basic one

top

Simpler real-time monitor.

Quick RAM summary

free -h

Live updating RAM view

watch -n 1 free -h

This refreshes every second.

⸻

10) Clearing cache and memory-related maintenance

Sync data first

sudo sync

Clear Linux caches

echo 3 | sudo tee /proc/sys/vm/drop_caches

This clears:

* page cache
* dentries
* inodes

Clean APT package cache

sudo apt clean

Remove unused packages

sudo apt autoremove -y

⸻

11) Network discovery and IP checking

These were a big part of your Kali networking learning.

Show IP addresses

ip a

Show routing table

ip route

Ping a site

ping google.com

Check public IP

curl ifconfig.me

or

curl ipinfo.io/ip

Scan your own machine

nmap localhost

or

nmap 127.0.0.1

Scan your hotspot subnet

Example:

nmap 172.20.10.0/28

Use this only on networks you own or have permission to test.

Scan service versions

nmap -sV 172.20.10.1

This tries to identify services and versions.

⸻

12) Wireshark and packet tools

Launch Wireshark

wireshark

Terminal packet capture tool

tcpdump

CLI version of Wireshark

tshark

These are your network visibility tools.

⸻

13) Browser and web session basics

Chromium install

sudo apt install chromium

Firefox ESR install

sudo apt install firefox-esr -y

General browser cleanup is usually done from browser settings, not terminal.

⸻

14) GRUB and boot menu basics

These came up a lot during the USB adventure.

Enter GRUB command line

At the GRUB menu, pressing c can open the command shell.

Return to normal menu

normal

You type that inside the GRUB command shell.

Check boot parameters inside Linux

cat /proc/cmdline

Very important for checking whether persistence is actually active.

⸻

15) Checking whether Kali persistence is active

These are the commands that finally proved persistence was working.

See boot parameters

cat /proc/cmdline

You want to see the word:

persistence

See whether the persistence partition is mounted

mount | grep persistence

Check label on the partition

sudo blkid

Look for:

LABEL="persistence"

Check the persistence partition contents

sudo mount /dev/sda3 /mnt/persistence
ls /mnt/persistence
cat /mnt/persistence/persistence.conf

Create the persistence config file

echo "/ union" | sudo tee /mnt/persistence/persistence.conf

⸻

16) Testing whether persistence works

These are the clean tests.

Make a folder

mkdir ~/PERSIST_TEST

Make a text file

echo "Persistence works" > ~/PERSIST_TEST/test.txt

Make a file on the desktop

touch ~/Desktop/hello.txt

Install a package and reboot

Example:

sudo apt install htop -y

If it remains after reboot, persistence is working.

Check if htop exists

htop

If it opens after reboot, that is a great sign.

⸻

17) Chrome/Chromium package issues

If something says “unable to locate package,” this is the usual fix:

sudo apt update

Then try again:

sudo apt install htop -y

or

sudo apt install chromium

Sometimes a package name changes slightly, so searching helps:

apt search chromium

⸻

18) Working with mounts

Create a mount folder

sudo mkdir -p /mnt/persistence

Mount a partition

sudo mount /dev/sda3 /mnt/persistence

Unmount

sudo umount /mnt/persistence

Mount help

mount --help

Useful when syntax feels confusing.

⸻

19) Basic troubleshooting commands

See kernel/boot messages

dmesg

Show last system logs

journalctl -xe

Check system services

systemctl status servicename

Reboot

sudo reboot

Shutdown

sudo shutdown now

⸻

20) Permissions and ownership

Good for Linux fundamentals and your CSE syllabus too.

chmod +x script.sh

Makes a file executable.

chmod 644 file.txt

Common file permission mode.

chmod 755 foldername

Common executable folder mode.

sudo chown user:user file.txt

Changes file ownership.

⸻

21) Shell scripting basics

These came up in the Linux basics part of your journey.

Simple script

#!/bin/bash
echo "Hello"

Run a script

bash script.sh

Or after making it executable:

./script.sh

⸻

22) Python and pip basics

python3 --version
pip --version
python3 script.py
pip install requests
pip install scapy

Useful for automation and network tooling.

⸻

23) Hotspot / IP discovery

These showed your phone hotspot network setup.

Show your device IP

ip a

Look for:

inet 172.20.10.3/28

Show gateway

ip route

Look for:

default via 172.20.10.1

Show public IP

curl ifconfig.me

⸻

24) Browser and app persistence checks

These are very practical when testing your Kali USB.

Install a package

sudo apt install htop -y

Reboot and check if it stays

htop

Open Firefox and see whether tabs restore

That’s a behavioral sign that persistence is saving session data.

⸻

25) Simple “what should I use where?” guide

This is not a command, but it matters as much as any command.

Ubuntu

Use Ubuntu for:

* coding
* OpenCV
* school work
* daily browsing
* writing
* stable development

Kali

Use Kali for:

* network discovery
* Wireshark
* Nmap
* lab experiments
* cybersecurity practice
* controlled tests on your own systems

⸻

26) Mini command map for your setup

If you forget everything else, remember this map:

Check system

whoami
pwd
ls
uname -a

Check disk

lsblk
df -h
sudo blkid

Check memory

free -h
htop

Check network

ip a
ip route
curl ifconfig.me
nmap localhost

Install tools

sudo apt update
sudo apt install package-name

Persistence

cat /proc/cmdline
mount | grep persistence
ls /mnt/persistence
cat /mnt/persistence/persistence.conf

⸻

27) One clean Kali persistence workflow

Here is the whole flow in one place:

sudo mkfs.ext4 -L persistence /dev/sda3
sudo mkdir -p /mnt/persistence
sudo mount /dev/sda3 /mnt/persistence
echo "/ union" | sudo tee /mnt/persistence/persistence.conf
sudo umount /mnt/persistence

Then boot Kali using:

Live system (persistence)

⸻

28) One clean USB imaging workflow

lsblk
sudo dd if=~/Downloads/yourimage.iso of=/dev/sdX bs=4M
sync

Replace:

* yourimage.iso with your ISO filename
* /dev/sdX with the actual USB device

⸻

29) The most useful “daily Kali” commands

If you only keep a handful, keep these:

htop
free -h
ip a
ip route
nmap localhost
sudo apt update
sudo apt install package-name
wireshark
curl ifconfig.me
cat /proc/cmdline

⸻

30) Final memory trick

Think of your setup like this:

* Ubuntu = build and study
* Kali = inspect and test
* USB persistence = save the lab
* Nmap/Wireshark = your eyes
* htop/free = your system dashboard

That’s your base kit.
