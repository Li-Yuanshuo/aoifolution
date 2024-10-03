# A Beginner's Guide for Aoifolution

Children today have an entirely different way of interacting with electronic devices. Most of them own a smartphone, tablet, or even a VR device earlier than they get a laptop. To them, it feels more intuitive to swipe and tap on a touchscreen than to use other input methods. 

However, in the past, keyboards were the primary way to interact with electronic devices (after teletype machines and punch cards). Even the mouse only became widespread after the advent of graphical user interfaces (GUI). 

So, you might find **command-line** operating systems unfamiliar, but that's perfectly fine — everyone has a beginning.

<br><br>
___

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

## **1. SSH to Aoifolution**
   
   SSH (Secure Shell Protocol)  is a most notable applications for remote login and command-line execution.
   ```bash
   ssh <username>@aoifolution.gen.tcd.ie
   ```
>TIPS: Nothing will appear on the screen when you enter your password, so don't freak out.

>TIPS: Use up ⬆ and down ⬇ arrow to select the command you typed before so you don't need to type it again

<br><br>

## **2. Wandering in the file system**

   ```bash
   liyuanshuo@aoifolution:~$
   ```
   After you log in to Aoifolution, this is what you will see first. The tilde symbol `~` represents your home directory, which is where you will start every time you log in.
   <br><br>
   
### ***A. But where exactly is your home directory? try:***
   ```bash
   liyuanshuo@aoifolution:~$ pwd
   /home/liyuanshuo
   ```
   `pwd` means `print work directory`, it shows the current directory where you are right now. It works in everywhere.

   `home/` is the home directory for Aoifolution, and you are one of the users under it.
   <br><br>

### ***B. What do you have in your home directory? try:***
   ```bash
   liyuanshuo@aoifolution:~$ ls

   
   ```
   **Nothing!!** It makes sense if this is your first time log in your server, becasue you have nothing yet.
   
   `ls` means `list`. It list all files and folders in the current directory.
   <br><br>

### ***C. Where shoud I go? try:***
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
   <br><br>
   
### ***D. When were they here?***
   
   If you want to know infomation about them and their directory, you can try:
   ```bash
   ls -l
   ```
   Here, `ls -l` shows more detailed **l**ong format of the files and folders, including permission, owner, size and so on.
   
   `-l` is the options/flags of the command. It modify the details of the command. It could be a single letter such as  `-l` or a full word   `--all`. 

   >NOTE: **command, arguments and options/flags constitute most of command lines. You can chech how to use a command by `command --help` or `command -h` or `man command` (man means manual) to read the manual**
   
   >TASK: Use `ls --help` and `man ls` to read the manual of `ls` and compare the difference.
   <br><br>
   
### ***E. Homecoming***
   
   Now, before you mess up other people's files, it is better to go back your own home directory. There are a couple different way to do it:
   
   ```bash
   #do you remember which command we used to change directory?
   cd <your_user_name> # since you are in the home directory of aoifolution, you should be able to go to anyone's directory, including yourself's
   cd ~ # remember, `~` always means your own home directory
   cd # if you don't have any argument after `ls`, the default directory is your home directory
   ```
   >TIPS: You **DON'T** have to type the complete file or folder name when you write in commond line. Try to press `TAB` key after you type the first few letters. The `TAB` key is usually located above the Caps Lock key. `TAB` can auto-complete the full name for you. It is very user-friendly for someone who cannot spell like me.
   >TIPS: Double `TAB` when you need to see all the possible files or folder options, so you don't need to `ls` again in the middle of writing a command
   <br><br>
   
   
### ***F. Path, path, path***

   Now you’ve learned how to navigate to different directories, how to see what’s inside each folder, and how to check your current location. You also learned that in the file system, `..` refers to the parent directory (one level up from the current directory), `~` is your home directory, and `.` represents the current directory (which you can see when using the pwd command).

   It may not seem as fun as simply double-clicking in a graphical user interface (GUI) like Finder, and you're right—it takes more effort.
   Instead of clicking around, you need to type the full path to tell the system where to go. There are two types of paths:

   -**Absolute Path**: An absolute path starts from the root directory (/) and specifies the full path to a file or directory. It remains the same regardless of the current working directory.

      **Example**: /home/user/documents/file.txt

   -**Relative Path**: A relative path starts from the current working directory and provides a path to a file or directory relative to that location. It uses . or .. to start.

      **Example**: ./documents/file.txt or ../file.txt

   As you may have noticed, different directory levels in the file system are separated by `/`.
   

<br><br>
___
   Now you should be able to navigate around the server and explore its contents. Try completing the following exercises:

   - [x] Go back to your home directory.
   - [x] List the contents of the parent directory while you are in your home directory.
   - [x] List the contents of the `/shared` folder and check their details while still in your home directory.
   - [x] Change the current directory to the folder inside `/shared` that starts with `aoifo` using a one-line command (use double TAB for autocompletion).
   - [x] Check where you are now (your current directory).
   - [x] Return to your home directory using a different command from the first exercise.
   
<details>
  <summary>click to see the answers</summary>
   
  ```bash
   cd
   ls ../
   ls -l ../shared
   cd ../shared/aoifolution_exercises/
   pwd
   cd ~
  ```
  
</details>
   
___
<br><br>

## **3.Make some changes**
Looks like your home directory is still empty. Lets make some changes.

### ***A. make a folder***

First, lets make a folder called `elle`(don't ask why) then go in there. The command is `mkdir`, refers to  `MaKe DIRectory`. 
```bash
mkdir elle
cd elle
```
You can make multiple folders in the same time 
```bash
mkdir elle1 elle2
```
You can make folder in another exist folder
```bash
mkdir elle1/elle3
```
However you cannot make folder in an not exist folder
```bash
mkdir elle4/elle5
mkdir: cannot create directory 'elle4/elle5': No such file or directory
```
### ***B. make a file***
The simplest way to make an empty file is `touch`
```bash
touch worm # why would anyone do this?
ls
```
You can see there is a new file called `worm` but it is empty. Usually, if you want to build a file, you do want to enter something to save in it. Here, you need Text editor Software to do it. 

The most powerful text editor is called **Vim**. 

But we are not going to use it cause it is way complicated. 

Here we use a lighter and simple editer called `nano`

```bash
nano worm
```
You would see yourself inside the eidter interface. Type something like `Worms are cool`, and `ctrl` + `x` to exit. Press **y** to save the change and  `enter` to save in the same file 
>TIPS: If you `nano` a not exist file, nano will build a new one. But if you didn't do anything and exit, the empty file won't be save.
>
>NOTE: The best way to edit a txt/tsv/csv file is use sofewares in your own local computer after you set up the SSHF (personally experience)

### ***C. copy, paste and move***
Copy and paste is one commond in linux: `cp`. It use as `cp` [what] [to where] 
```bash
cp worm elle1/
ls elle1/
worm
```
If you give a new file name instead of a folder in the second argument, `cp` will copy the file **AND** rename it to the new name. 
```bash
cp worm elle1/worm2
ls elle1/
worm  worm2
```
`mv`, which is move a file to some where, uses the same rule as `cp`
```
mv worm elle2/
mv elle1/worm elle2/worm3
ls
elle1  elle2
ls elle1
worm2
ls elle2
worm  worm3
```
>NOTE: `mv` command actually do two things at once: copy file to DEST and remove the orginal file.

### ***D. Rename a file***
Command line doesn't have a function for rename!!!

But think about this: the logic of **rename** is to move a file with OLD_NAME in to a file with NEW_NAME. Do you know how to do it now?

Try to renmae `worm3` in `/elle2` as `worm2`

<details>
  <summary>the answers</summary>
   
  ```bash
    mv elle2/worm3 elle2/worm2
    ls elle2
    worm  worm2
  ```
</details>

### ***E. DELETE（permanently）***
The command for delete is `rm`, refers to remove a file. 
```bash
rm elle2/worm3
ls elle2
worm
```
Now try it on a directory:
```bash
rm elle2
rm: cannot remove 'elle2': Is a directory
```
It is not work!!! You **CANNOT** get rid of elle. 

Check how to solve the issue with `rm --help`:

<details>
  <summary>the answers</summary>
   
  ```bash
    rm elle2 -r
    ls
  ```
</details>

>WARNING: Be **cautious** when using the rm command in Linux. It **permanently** deletes files and directories without recovery, so mistakes can lead to irreversible data loss.
>If you are not sure the data is useful or not, move it to somewhere first.

>NOTE: As opposed to `mkdir`, deleted a folder is `rmdir`, but it only function on empty folder

<br><br>
___
   Now you should be able to do the basic operation . Try completing the following exercises:

   - [x] List the files in `/home/shared/aoifolution_exercises`
   - [x] Copy the files there to `/elle` while you are in your home directory (use double TAB for autocompletion).
   - [x] rename the `.fasta` file to `.faa` file
   - [x] Delete the `.faa` file that you just renamed
   - [x] Move the `.gff3` file from `/elle` to your home directory 
   - [x] Remove the entire `/elle` folder
   - [x] Make a folder called `worms`
   - [x] Use `nano` to make a new file called `worm1`, write `This worm is cool` and save it. Move it in the `worms` folder
   - [x] Stay in the home directory, and make a new file in the `worms` folder called `worm2`, write `This worm is NOT cool` and save it.
     
<details>
  <summary>click to see the answers</summary>
   
  ```bash
   ls /home/shared/aoifolution_exercises/
   cp /home/shared/aoifolution_exercises/Homo_sapiens.GRCh38.112.ensembl.fasta elle/
   cp /home/shared/aoifolution_exercises/Homo_sapiens.GRCh38.112.ensembl.gff3 elle/
   mv elle/Homo_sapiens.GRCh38.112.ensembl.fasta elle/Homo_sapiens.GRCh38.112.ensembl.faa
   rm elle/Homo_sapiens.GRCh38.112.ensembl.faa
   mv elle/Homo_sapiens.GRCh38.112.ensembl.gff3 .
   rm elle -r
   mkdir worms
   nano worm1 # then type `This worm is cool` then `ctrl + x` and `enter`
   mv worm1 worms
   nano worms/worm2 # then type `This worm is cool` then `ctrl + x` and `enter`
  ```
  
</details>

___
<br><br>


## **4.View the file**

You should have a `.gff3` file, a `/worm` folder with a cool worm1 and a not cool worm2 in it. 

### ***A. Meow :cat:***

To quick view a file, you can use `cat` command and the file you want to view. Now use it to see which worm is the cool worm:
```bash
cat worms/worm1
This worm is cool
cat worms/worm2
This worm is NOT cool
```

`cat` doesn't mean the meow cat :cat2:, but the short for **concatenate**, which use for concatenate files together and print on the screen. Try to use it on worm1 and worm2 
```bash
cat worms/worm1 worms/worm2
This worm is cool
This worm is NOT cool
```
Great! Now try to view the `.gff3` file:
```bash
cat Homo_sapiens.GRCh38.112.ensembl.gff3
```

<details>
  <summary>NOTE: ctrl + c kills WHATEVER job is running </summary>
   
   >NOTE: **MY EYES!! MY EYES!!**
   >
   >>NOTE: lesson 1: **Always** read the notes before you run a command
   >>
   >>>NOTE: lesson 2: **Never trust** others' data or scripts, or their personality.
  
</details>

### ***B. Head or tail***

Obviously, big files like `.gff3` can't be printed on the screen at once. Let's just use `head` command to view the first few rows of the `.gff3` file. 
```bash
head Homo_sapiens.GRCh38.112.ensembl.gff3
```
Here are the first 10 rows of the `.gff3` file. Use `head --help` to check how to view more or less rows:
<details>
  <summary>the answers</summary>
   
  ```bash
    head Homo_sapiens.GRCh38.112.ensembl.gff3 -n 20 # or 
    head -15 Homo_sapiens.GRCh38.112.ensembl.gff3
  ```
</details>

`tail` uses the same grammar as `head`, but shows the last few rows of a file. Try it:

<details>
  <summary>the answers</summary>
   
  ```bash
    tail Homo_sapiens.GRCh38.112.ensembl.gff3 -n 20 # or 
    tail -15 Homo_sapiens.GRCh38.112.ensembl.gff3
  ```
</details>

>NOTE: There is a useful option for `tail`, when you need to monitor a log file's updating, you could use `tail -f file` to check it file in realtime.

### ***C. Less is more***

It seems you still can't view the entire file continuously. `more` and `less` can help you view a file with a **srolling screen** effect. Try it:
```bash
more Homo_sapiens.GRCh38.112.ensembl.gff3
```

<details>
  <summary>NOTE</summary>
   
   >NOTE: haven't you learn anything yet? press q to quit the viewing
   >
   >>NOTE: use `more -- help` to read the manual before you apply the command
  
</details>

`Enter` or use arrow keys to rolling up and down. 

`less` perform the same function as `more` to view a big file. Try `less --help` and `less file` to see what is the different

   >NOTE: `less` was created after `more` to achive some function that `more` doesn't have, such as scrolling up. It is also faster and lighter
   >
   >NOTE: `less` open another window to view but `more` directly print on the screen. **`less` is recommended for viewing a file**


___
<br><br>

## **5.Useful tools**

### ***A. grep*** 

`grep` stands for **Global Regular Expression Print**. It is the most powerful command-line tool used (I think) to search for specific patterns or strings of text within files. You can use grep to find lines in a file that contain a certain word or match a specific pattern. Try to serch "worm" in a file:
```bash
grep "worm" worms/worm1
This worm is cool
```
>TIPS: You can use options with grep to make your searches more powerful:
>
>-i: Makes the search case-insensitive.
>
>-r: Recursively search through directories.
>
>-n: Show the line numbers along with the matched lines.

Previously we mentioned, for a command line, the command itself is crucial. Then you can add arguments to apply the function on and options/flags to modify the details of the function. Here we introduce **Redirection** `>` to save the output in a file:

```bash
cat worms/worm1 worms/worm2
This worm is cool
This worm is NOT cool
```
```bash
cat worms/worm1 worms/worm2 > worms.txt
cat worms.txt
This worm is cool
This worm is NOT cool
```
This is very useful when you want to save your output result. And it can be combined to use with other command.

Try to search "HOX" gene in the `.gff3` file, and save the output in a `HOX.tsv` file:

<details>
  <summary>the answers</summary>
   
  ```bash
    grep "HOX" Homo_sapiens.GRCh38.112.ensembl.gff3 > HOX.tsv
    head HOX.tsv
  ```
</details>

>NOTE: If you use `>>`, the new output will be appended in the end of the original file.

### ***B. Regular Expressions (RegEx)*** 

What does the **Regular Expressions** in `grep` mean? Basically, it is a grammar of patterns used to match character combinations in strings. They are an incredibly powerful tool for searching, matching, and manipulating text. 
Many Unix commands, like `grep`, `sed`, and `awk`, support RegEx for advanced pattern matching.

RegEx allows you to search for text that matches complex patterns rather than simple fixed strings. This is particularly useful when you don't know the exact form of the text you're searching for or when you're working with large datasets.

Considering RegEx is such a big part, I won't talk much about that here. But I recommend https://regex101.com/ to learn and test your RegEx.

### ***C. wc*** 

`wc` stands for **Word Count**, but it does more than just counting words. It can count lines, words, and characters in a file. This is especially useful when dealing with large files and you need to quickly get a sense of their size or contents. Try:

```bash
wc worms/worm1
1 4 18 worms/worm1

```
This output shows:
- 1 line
- 4 words
- 18 characters

You can use specific options with wc:

- `-l`: Count lines only.
- `-w`: Count words only.
- `-c`: Count characters only.

