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

>TIPS: Use up ⬆ and down ⬇ arrow to select the command you typed before so you don't need to type it again

2. Wandering in the file system
   ```bash
   liyuanshuo@aoifolution:~$
   ```
   After you log in to Aoifolution, this is what you will see first. The tilde symbol `~` represents your home directory, which is where you will start every time you log in.
   <br>
   
   ***1. But where exactly is your home directory? try:***
   ```bash
   liyuanshuo@aoifolution:~$ pwd
   /home/liyuanshuo
   ```
   `pwd` means `print work directory`, it shows the current directory where you are right now. It works in everywhere.

   `home/` is the home directory for Aoifolution, and you are one of the users under it.
   <br>

   ***2. What do you have in your home directory? try:***
   ```bash
   liyuanshuo@aoifolution:~$ ls

   
   ```
   **Nothing!!** It makes sense if this is your first time log in your server, becasue you have nothing yet.
   
   `ls` means `list`. It list all files and folders in the current directory.
   <br>

   ***3. Where shoud I go? try***
   ```bash
   liyuanshuo@aoifolution:~$ cd ..

   ```
   `cd` means `change current directory`, and `..` means the parent directory of the current.

   `cd` is the **command** part of this command line, it is the core of each command and it tells the computer what function you want to use. `..` is the **Arguments** part, it goes after the command to tell the computer the objects that you want to function on. It can be files, path, directory or others.
   <br><br>

   >TASK: Now try to find out where are you now
   
   >TASK: List all files and folder in the current directory
   <br>

   **Voilà**, you can see every users on Aoifolution and each person have one home directory. You could find yourself and maybe other peoples' name in it.
   <br>
   
   ***4. When were they here?***
   
   If you want to know infomation about them and their directory, you can try:
   ```bash
   ls -l
   ```
   Here, `ls -l` shows more details of the files and folders, including permission, owner, size and so on.
   
   `-l` is the options/flags of the command. It modify the details of the command. It could be a single letter such as  `-l` or a full word   `--all`. 

   >NOTE: **command, arguments and options/flags constitute most of command lines. You can chech how to use a command by `command --help` or `command -h` or `man command` (man means manual) to read the manual**
   
   >TASK: Use `ls --help` and `man ls` to read the manual of `ls` and compare the difference.
   <br>
   
   ***5. Homecoming***
   
   Now, before you mess up other people's files, it is better to go back your own home directory. There are a couple different way to do it:
   
   ```bash
   #do you remember which command we used to change directory?
   cd <your_user_name> # since you are in the home directory of aoifolution, you should be able to go to anyone's directory, including yourself's
   cd ~ # remember, `~` always means your own home directory
   cd # if you don't have any argument after `ls`, the default directory is your home directory
   ```
   >TIPS: You **DON'T** have to type the complete file or folder name when you write in commond line. Try to press `TAB` key after you type the first few letters. The `TAB` key is usually located above the Caps Lock key. `TAB` can auto-complete the full name for you. It is very user-friendly for someone who cannot spell like me.
   >TIPS: Double `TAB` when you need to see all the possible files or folder options, so you don't need to `ls` again in the middle of writing a command

    <br>
   
   ***6. path, path, path***

   Now you’ve learned how to navigate to different directories, how to see what’s inside each folder, and how to check your current location. You also learned that in the file system, `..` refers to the parent directory (one level up from the current directory), `~` is your home directory, and `.` represents the current directory (which you can see when using the pwd command).

   It may not seem as fun as simply double-clicking in a graphical user interface (GUI) like Finder, and you're right—it takes more effort.
   Instead of clicking around, you need to type the full path to tell the system where to go. There are two types of paths:

   -**Absolute Path**: An absolute path starts from the root directory (/) and specifies the full path to a file or directory. It remains the same regardless of the current working directory.
         **Example**: /home/user/documents/file.txt

   -**Relative Path**: A relative path starts from the current working directory and provides a path to a file or directory relative to that location. It uses . or .. to start.
         **Example**: ./documents/file.txt or ../file.txt

Now you should 

<details>
  <summary>点击显示答案</summary>
  
  答案是：42
  
</details>


