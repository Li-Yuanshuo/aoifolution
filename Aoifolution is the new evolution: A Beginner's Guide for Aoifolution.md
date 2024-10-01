# A Beginner's Guide for Aoifolution

Children today have an entirely different way of interacting with electronic devices. Most of them own a smartphone, tablet, or even a VR device earlier than they get a laptop. To them, it feels more intuitive to swipe and tap on a touchscreen than to use other input methods. 

However, in the past, keyboards were the primary way to interact with electronic devices (after teletype machines and punch cards). Even the mouse only became widespread after the advent of graphical user interfaces (GUI). 

So, you might find **command-line** operating systems unfamiliar, but that's perfectly fine — everyone has a beginning.
___
<br><br>
_**But first,**_
## **_Why_** is the **command-line tool** used in bioinformatics?

After getting used to modern smart devices, going back to using a keyboard for input might seem primitive. But why do we still do it? 

While many bioinformatics tools provide **graphical user interfaces (GUIs)** (such as MEGA and Geneious), making them more user-friendly for researchers, these tools, along with the hardware they run on (your personal computer), can become very limited when processing large datasets. 
The same computation that might take years on your local computer can be completed in hours on a **high-performance computing (HPC)** system like Aoifolution. 
<br><br>

Most HPC systems operate on **Linux/Unix environments**, where **command-line interfaces (CLIs)** are the standard mode of interaction. This method offers several advantages:


**1. Efficiency and Flexibility**
   
The command line allows you to precisely control complex settings in bioinformatics software through various parameters, and it enables batch processing via scripting. This is crucial for handling large-scale biological data, such as transcriptomic or genomic analyses. By fully utilizing HPC resources, you can significantly improve your efficiency.

**2. Reproducibility and Compatibility**
   
Reproducibility is a cornerstone of any experiment, meaning that under the same conditions, others should be able to reproduce the same results. The command line provides a simple yet comprehensive way to document bioinformatics analysis protocols, unlike vague GUI instructions like “right-click this icon and select that option.” Moreover, software interfaces can vary across operating systems, but command-line tools are often **cross-platform compatible**, allowing you to run the same workflows on different systems (Linux, macOS, Windows) without worrying about platform-specific differences.

**3. Development, Maintenance, and Integration**
   
For these reasons, most bioinformatics software is designed for command-line interaction. Designing and maintaining a GUI is more complex, as it requires attention to compatibility and resource usage. Command-line tools, however, allow developers to focus on core functionality. Additionally, they are easier to integrate into scripts, pipelines, and automated processes, making them more versatile for large-scale or repetitive tasks.

<br><br>
___
## **_What_** is **Aoifolution**?

As we said, Aoifolution is a high-performance computing (HPC) system.  Here is its tech-specs: 
- Dell PowerEdge R740, purchased April 2021
- 2 x Intel Xeon Silver 4210R CPU @ 2.40GHz (10 cores, 20 threads)
- 2 x 500 GB SSD 
- 44 TB RAID5 (5 x 12 TB + 1 spare)
- 384 GB RAM
- 20 cores and 40 threads in total

As you can see, Aoifolution is probably 10 times more powerful than your local computer. It is more like a **cluster** of many computers.

Everytime when you log in Aoifolution (SSH), it pops the system information: 
```bash
li@LOCAL ~
$ ssh liyuanshuo@aoifolution.gen.tcd.ie
Welcome to Ubuntu 20.10 (GNU/Linux 5.8.0-53-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

3 updates can be installed immediately.
0 of these updates are security updates.
To see these additional updates run: apt list --upgradable

Your Ubuntu release is not supported anymore.
For upgrade information, please visit:
http://www.ubuntu.com/releaseendoflife

New release '22.04.5 LTS' available.
Run 'do-release-upgrade' to upgrade to it.

*** System restart required ***
No mail.
Last login: Mon Sep 30 17:27:00 2024 from 10.6.48.122
```
It shows Aoifolution is using Ubuntu 20.10.
<br><br>

### Linux? Unix? Ubuntu? Kernel? OS?

> If you don’t have a strong computer background, all these computer terms might feel overwhelming. Let’s break them down in the simplest way possible.
>
> After you assemble a computer (for example, you’ve put together an Aoifolution based on the hardware specifications above), the next big question is: how do you give it instructions? 
Unfortunately, Aoifolution doesn’t have eyes or ears to see or hear your commands, nor does it have a brain to process them (like Elle). You need an operating system to communicate with Aoifolution and make it understand your instructions.
> 
> Think of the operating system as a translator. It gathers your input (via applications), translates it into a language the hardware can understand (via the kernel), and then sends the instructions to Aoifolution. The operating system (OS) consists of two main parts: **applications** (which talk to users) and the **kernel** (which talks to the machine).
> 
> A long time ago (in 1969), Bell Labs developed an operating system called [UNIX](https://en.wikipedia.org/wiki/Unix). It was so efficient and versatile that it became a potential universal operating system, influencing the design and logic of many future systems. These systems are known as Unix-like systems.
Examples include GNU/Linux OS (where the kernel is Linux) and macOS (where the kernel is XNU).
> 
> > This explains why the command line in Linux and macOS is often compatible, but Windows is not, as its kernel is based on Windows NT.
> 
> Because the GNU/Linux OS is an open-source project, it has attracted a large number of developers who contribute to its growth. The kernel is [Linux](https://en.wikipedia.org/wiki/Linux_kernel)，and the applications and system tools are provided by the [GNU](https://en.wikipedia.org/wiki/GNU) project. 
> 
> The GNU project offers essential system tools, libraries, compilers, and shells that the Linux kernel does not provide. Meanwhile, Linux provides the kernel that GNU lacks, making these two parts complementary. Therefore, what we often refer to as the "Linux" operating system is more accurately called the "GNU/Linux" operating system.
> 
> On top of this, many developers have continued to improve the operating system to give users a more complete experience, resulting in what we know as Linux distributions. The most well-known and long-standing distribution is **Debian**, which adds features like the software management system **APT** (Advanced Package Tool) to the base operating system.
> 
> Debian also serves as the foundation for other popular distributions, including **Ubuntu** (which powers Aoifolution), Raspberry Pi OS (used in our microscope), and many others.
> 
> In summary, our Aoifolution is an **HPC** running **Ubuntu**, which is built on the **GNU/Linux OS**. This core system shares many of the same commands and functionality as other **Unix-like** systems, such as macOS.

<br><br><br>
___
# **_How_** to use Aoifolution 

After all the old man's rambling, this is finally the session to teach you how to handle Aoifelution.

1. SSH to Aoifolution
   SSH (Secure Shell Protocol)  is a most notable applications for remote login and command-line execution.
   ```bash
   ssh <username>@aoifolution.gen.tcd.ie
   ```
>TIPS: Nothing will appear on the screen when you enter your password, so don't freak out.

>TIPS: Use up ⬆ and down ⬇ arrow to select the commond you typed before so you don't need to type it again


