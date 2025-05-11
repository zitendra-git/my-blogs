---
title: "🐧 Ultimate Guide to Linux Directories & Files"
seoTitle: "Mastering the Linux File System: Deep Dive into Directories, Files ."
seoDescription: "A complete beginner-to-advanced guide to Linux file system hierarchy. Learn every directory’s purpose, key files, and shortcuts with simple explanations."
datePublished: Sun May 11 2025 17:54:15 GMT+0000 (Coordinated Universal Time)
cuid: cmajye3ab000c09jp8gtrbrpf
slug: ultimate-guide-to-linux-directories-and-files
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1746985955433/b707d12f-4d44-49b9-958e-4278119ac534.png
tags: linux, linux-basics, linux-file-system

---

If you’re stepping into the world of Linux, understanding its **file system hierarchy** is crucial. Think of it like learning your way around a city—once you know where everything is, using it becomes second nature. This guide will take you from the **basics to expert-level** knowledge about Linux directories, their roles, important files, and even symbolic links (shortcuts).

## **🔍 What Is the Linux File System?**

The **Linux file system** is the structure where data is stored, organized, and accessed. Unlike Windows (which uses drive letters like C:, D:), Linux uses a **tree-like structure** starting at a single root directory: `/` .

### **🧾 Basic Terms to Know:**

* **Directory**: A folder used to group files.
    
* **File**: A data container (text, binary, config, etc.)
    
* **Root (**`/` **)**: The topmost directory in the hierarchy.
    
* **Symlink (Symbolic Link)**: A shortcut or reference to another file/directory.
    

## **🌲 The File System Tree Overview**

Everything starts from `/` (root). All files and folders branch out from here.

```bash
/
├── bin
├── boot
├── dev
├── etc
├── home
├── lib -> usr/lib
├── lib64 -> usr/lib64
├── media
├── mnt
├── opt
├── proc
├── root
├── run
├── sbin -> usr/sbin
├── srv
├── sys
├── tmp
├── usr
└── var
```

🔁 Notice: Some directories like `/lib` , `/sbin` , and `/bin` are now **symlinks** pointing to `/usr/lib` , `/usr/sbin` , and `/usr/bin` on modern Linux systems.

# **🧰 In-Depth Directory Breakdown**

Let’s explore each directory in detail with examples, real-world use, and shortcut (symlink) info.

## **📦** `/bin` **– Essential User Commands**

* **Purpose**: Contains basic executable programs and command-line tools required by all users.
    
* **Examples**: `ls` , `cp` , `mv` , `rm` , `cat`
    
* **Access**: Available to all users.
    
* **Important**: Needed during system recovery.
    

🔁 On newer distros, `/bin` is a symlink to `/usr/bin` .

## **⚙️** `/sbin` **– System Binaries**

* **Purpose**: Holds system-level utilities mainly used by the **root (admin)** user.
    
* **Examples**: `fsck` , `reboot` , `shutdown` , `ifconfig`
    
* **Access**: Restricted to root for system maintenance.
    

🔁 Typically symlinked to `/usr/sbin` .

## **🧠** `/boot` **– Boot Loader Files**

* **Purpose**: Contains all files required to boot the system.
    
* **Includes**: Kernel files (vmlinuz), initrd, grub config files.
    
* **Caution**: Messing with this can break your system!
    

📝 *Example files:*

```bash
/boot/grub/grub.cfg
/boot/vmlinuz-5.15.0
```

## **🧪** `/dev`  **– Device Files**

* **Purpose**: Represents system devices as files.
    
* **Type**: Virtual, dynamically managed by the kernel (udev).
    
* **Examples**:
    
    * `/dev/sda` → Hard disk
        
    * `/dev/tty` → Terminals
        
    * `/dev/null` → “Black hole” file
        
* 🧠 Why? Because in Linux, **everything is a file**—including hardware.
    

## **🔐** `/etc`  **– Configuration Files**

* **Purpose**: Houses all system-wide configuration files and directories.
    
* **DO NOT store personal data here**.
    
* **Examples**:
    
    * `/etc/passwd` : List of system users
        
    * `/etc/ssh/sshd_config` : SSH settings
        
    * `/etc/fstab` : Filesystem mount table
        

🧠 Most services (like networking, cron jobs, etc.) read their settings from `/etc` .

## **🏠** `/home`  **– User Home Directories**

* **Purpose**: Personal directories for every user (non-root).
    
* **Layout**: `/home/username/`
    
* **What’s Inside**: Documents, Pictures, Downloads, personal app settings
    

💡 Each user can modify files in their own home but not in others’ or system directories.

## **👑** `/root`  **– Root User’s Home**

* **Purpose**: Home directory of the **superuser**.
    
* **Not** to be confused with / (root of the file system).
    
* **Path**: `/root/` (not under /home!)
    

🛑 Only accessible by the root user.

## **🧬** `/lib` **and** `/lib64` **– Shared Libraries**

* **Purpose**: Contains essential shared libraries needed by binaries in /bin and /sbin.
    
* **64-bit Systems**: Use`/lib64` for 64-bit libraries.
    

🔁 These are **often symbolic links** to `/usr/lib` and `/usr/lib64` .

## **📂** `/media` **and** `/mnt` **– Mount Points**

* `/media` : Auto-mounted external devices (USBs, DVDs)
    
* `/mnt` : Temporary mount point for system admin (manual)
    

🧠 *Mounting* means linking a device to the file system so it becomes accessible.

## **💼** `/opt`  **– Optional Software Packages**

* **Purpose**: For third-party software that doesn’t fit into standard paths.
    
* **Example**: Google Chrome or proprietary software installations.
    

🗂️ Often used for large software suites.

## **🧾** `/proc` **– Process Info (Virtual Filesystem)**

* **Purpose**: Dynamic, virtual files showing system and process info.
    
* **Managed by**: Kernel
    
* **Examples**:
    
    * `/proc/cpuinfo` : CPU details
        
    * `/proc/meminfo` : Memory usage
        
    * `/proc/[PID]/` : Info about a specific process
        
* 🧠 These files **don’t exist on disk**—they’re created in real time!
    

## **🔁** `/run` **– Runtime Data**

* **Purpose**: Stores volatile runtime info (like PID files) needed between boot and services.
    
* **Cleared at**: Every reboot.
    
* **Used by**: systemd, network services, login sessions
    

## **🗃️** `/srv` **– Service Data**

* **Purpose**: Contains data for services like FTP, HTTP, etc.
    
* **Examples**:
    
    * `/srv/ftp/`
        
    * `/srv/www/`
        
* 👨‍💻 Useful for servers hosting public services.
    

## **⚠️** `/tmp` **– Temporary Files**

* **Purpose**: Temp files created by applications.
    
* **Auto-cleared**: On reboot or scheduled cleanup.
    
* **Examples**:
    
    * Download caches
        
    * Unzipped install files
        

🧼 Never store important data here!

## **🌐** `/usr`  **– User System Resources (Not “Home” Users)**

* **Purpose**: Contains application binaries, libraries, docs not critical to boot.
    
* **Structure**:
    
    * `/usr/bin` : User-level commands
        
    * `/usr/lib` : Libraries
        
    * `/usr/share` : Shared documentation, icons
        

💡 On modern distros, this is the **core of most Linux software**.

## **📊** `/var` **– Variable Files**

* **Purpose**: Data that changes frequently.
    
* **Includes**:
    
    * Logs (`/var/log` )
        
    * Mail spools
        
    * Print queues
        
    * Databases
        

📉 If your system runs out of space, `/var` is often the culprit.

# **🧩 Which Directories Are Symlinks?**

Here are the most common **symlinked directories**:

| **Directory** | **Symlink To** | **Purpose** |
| --- | --- | --- |
| `/bin` | `/usr/bin` | Basic commands |
| `/sbin` | `/usr/sbin` | System commands |
| `/lib` | `/usr/lib` | Shared libraries |
| `/lib64` | `/usr/lib64` | 64-bit libraries |

These symlinks ensure backward compatibility and maintain a cleaner structure under /usr.

## **📌 Key System Files to Know**

| **File** | **Description** |
| --- | --- |
| `/etc/passwd` | User account details |
| `/etc/shadow` | Encrypted user passwords |
| `/etc/fstab` | Auto-mount drives |
| `/etc/hostname` | System hostname |
| `/etc/hosts` | Local DNS mappings |
| `/var/log/syslog` | System logs |
| `/proc/cpuinfo` | CPU info |
| `/etc/resolv.conf` | DNS resolver settings |

## **🧭 Why Learning the Linux File System Matters**

Mastering the file system allows you to:

✅ Troubleshoot faster

✅ Understand where apps store data

✅ Secure your system better

✅ Automate tasks using the terminal

✅ Feel confident working with Linux 💪