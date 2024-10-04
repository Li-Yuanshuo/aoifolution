# A Beginner's Guide for Aoifolution

Children today have an entirely different way of interacting with electronic devices. Most of them own a smartphone, tablet, or even a VR device earlier than they get a laptop. To them, it feels more intuitive to swipe and tap on a touchscreen than to use other input methods.

However, in the past, keyboards were the primary way to interact with electronic devices (after teletype machines and punch cards). Even the mouse only became widespread after the advent of graphical user interfaces (GUI).

So, you might find **command-line** operating systems unfamiliar, but that's perfectly fine — everyone has a beginning.

<br><br>
___

_**But first,**_
## **_Why_** is the **command-line tool** used in bioinformatics?

After getting used to modern smart devices, going back to using a keyboard for input might seem primitive. But why do we still do it?

While many bioinformatics tools provide **graphical user interfaces (GUIs)** (such as MEGA and Geneious), making them more user-friendly for researchers, these tools, along with the hardware they run on (your personal computer), can become very limited when processing large datasets. The same computation that might take years on your local computer can be completed in hours on a **high-performance computing (HPC)** system like Aoifolution.

<br>

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

Aoifolution is a high-performance computing (HPC) system. Here are its tech specs: 
- Dell PowerEdge R740, purchased April 2021
- 2 x Intel Xeon Silver 4210R CPU @ 2.40GHz (10 cores, 20 threads)
- 2 x 500 GB SSD 
- 44 TB RAID5 (5 x 12 TB + 1 spare)
- 384 GB RAM
- 20 cores and 40 threads in total

As you can see, Aoifolution is probably 10 times more powerful than your local computer. It is more like a **cluster** of many computers.

Every time you log into Aoifolution (SSH), you will see system information like this:

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

After all the old man's rambling, now it's time to teach you how to use Aoifolution.

## **1. SSH to Aoifolution**
   
   SSH (Secure Shell Protocol)  is an essential tool for remote login and command-line execution.
   ```bash
   ssh <username>@aoifolution.gen.tcd.ie
   ```
If this is your first time connect to Aoifolution, you will see this: 
```bash
The authenticity of host '192.168.1.10' can't be established.
ECDSA key fingerprint is SHA256:abc123....
Are you sure you want to continue connecting (yes/no)?
```
Don't be panic. Type `yes` and press Enter. This will add the remote device's fingerprint to your known hosts file, allowing future connections.

>TIPS: Nothing will appear on the screen when you enter your password, so don't freak out.

>TIPS: Use up ⬆ and down ⬇ arrow to select the command you typed before, so you don't need to type it again

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
   `pwd` means `print work directory`. It shows the current directory you are in.

   `home/` is the home directory for Aoifolution, and you are one of the users under it.

   >NOTE: **directory? folder?**
>
> Folder and directory are essentially the same thing, but the terms are used in different contexts:
> Folder is more commonly used in graphical user interfaces (GUIs), like in Windows or macOS, where files and directories are represented visually as folders.
> Directory is used more often in command-line interfaces (CLI) or Unix/Linux environments. It refers to the same concept: a container that organizes files and other directories.

   <br><br>

### ***B. What do you have in your home directory? try:***
   ```bash
   liyuanshuo@aoifolution:~$ ls
   
   ```
   **Nothing!!** It makes sense if this is your first time logging into the server, because you have nothing yet.
   
   `ls` means "list". It lists all files and folders in the current directory.
   <br><br>

### ***C. Where shoud I go? try:***
   ```bash
   liyuanshuo@aoifolution:~$ cd ..

   ```
   `cd` means `change current directory`, and `..` means the parent directory of the current one.

   `cd` is the **command** part of this command line, it is the core of each command and tells the computer what function you want to use. `..` is the **argument** part, it goes after the command to tell the computer the objects that you want to function on. It can be files, paths, directories, or others.
   <br><br>

   >TASK: Now try to find out where you are now.
   
   >TASK: List all files and folders in the current directory.
   <br>

   **Voilà**, you can see every user on Aoifolution, and each person has one home directory. You might find yourself and maybe other people’s names in it.
   <br><br>
   
### ***D. When were they here?***
   
   If you want to know more information about the files and their directory, you can try:
   ```bash
   ls -l
   ```
   Here, `ls -l` shows more detailed **l**ong format of the files and folders, including permissions, owner, size, and so on.
   
   `-l` is the **options/flags** of the command. It modifies the details of the command. It could be a single letter, such as  `-l`, or a full word `--all`. 

   >NOTE: **command, arguments and options/flags constitute most of command lines. You can chech how to use a command by `<command> --help` or `<command> -h` or `man <command>` (man means manual) to read the manual**
   
   >TASK: Use `ls --help` and `man ls` to read the manual of `ls` and compare the difference.
   <br><br>
   
### ***E. Homecoming***
   
   Now, before you mess up other people's files, it is better to go back to your own home directory. There are a couple of different ways to do it:
   
   ```bash
   #do you remember which command we used to change directory?
   cd <your_user_name> # since you are in the home directory of aoifolution, you should be able to go to anyone's directory, including yourself's
   cd ~ # remember, `~` always means your own home directory
   cd # if you don't have any argument after `ls`, the default directory is your home directory
   ```
   >TIPS: You **DON’T** have to type the complete file or folder name when you write in the command line. Try to press the `TAB` key after typing the first few letters. The `TAB` key is usually located above the `Caps Lock` key. `TAB` can auto-complete the full name for you. It’s very user-friendly for someone who cannot spell like me.
   >
   >TIPS: Double `TAB` when you need to see all the possible file or folder options, so you don’t need to `ls` again in the middle of writing a command.
<br><br>
   
   
### ***F. Path, path, path***

Now you’ve learned how to navigate to different directories, see what’s inside each folder, and check your current location. You also learned that in the file system, `..` refers to the parent directory (one level up from the current directory), `~` is your home directory, and `.` represents the current directory (which you can see when using the pwd command). The address of a file or folder in the file system is called **path**, showing how to navigate to it from the root directory.

It may not seem as fun as simply double-clicking in a graphical user interface (GUI) like Finder, and you're right—it takes more effort. Instead of clicking around, you need to type the full path to tell the system where to go. There are two types of paths:

   -**Absolute Path**: An absolute path starts from the root directory (/) and specifies the full path to a file or directory. It remains the same regardless of the current working directory.

      **Example** : /home/user/documents/file.txt

   -**Relative Path**: A relative path starts from the current working directory and provides a path to a file or directory relative to that location. It uses . or .. to start.

      **Example**: ./documents/file.txt or ../file.txt

As you may have noticed, different directory levels in the file system are separated by `/`.
   

<br><br>
___
   Now you should be able to navigate around the server and explore its contents. Try completing the following exercises:

   - [x] Go back to your home directory.
   - [x] List the contents of the parent directory while you are in your home directory.
   - [x] List the contents of the `/home/shared` folder and check their details while still in your home directory.
   - [x] Change the current directory to the folder inside `/home/shared` that starts with `aoifo` using a one-line command (use double TAB for autocompletion).
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
However you cannot make folder in an non-exist folder
```bash
mkdir elle4/elle5
mkdir: cannot create directory 'elle4/elle5': No such file or directory
```
### ***B. make a file***

>NOTE: A file is a container that stores data, such as text, images, videos, or executables. Files are the basic unit of storage in a computer system.

The simplest way to make an empty file is `touch`
```bash
touch worm # why would anyone do this?
ls
```
You can see there is a new file called `worm` but it is empty. Usually, if you want to build a file, you do want to enter something to save in it. Here, you need **Text editor Software** to do it. 

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
Copy and paste is one command in linux: `cp`. It use as `cp` [what] [to where] 
```bash
cp worm elle1/
ls elle1/
> worm
```
If you give a new file name instead of a folder in the second argument, `cp` will copy the file **AND** rename it to the new name. 
```bash
cp worm elle1/worm2
ls elle1/
> worm  worm2
```
`mv`, which is move a file to some where, uses the same rule as `cp`
```
mv worm elle2/
mv elle1/worm elle2/worm3
ls
> elle1  elle2
ls elle1
> worm2
ls elle2
> worm  worm3
```
>NOTE: `mv` command actually do two things at once: copy file to DEST and remove the orginal file.

### ***D. Rename a file***
Command line doesn’t have a dedicated function for renaming!

But think about this: the logic of **renaming** is to move a file with OLD_NAME in to a file with NEW_NAME. Do you know how to do it now?

Try to renmae `worm3` in `/elle2` as `worm2`

<details>
  <summary>the answers</summary>
   
  ```bash
    mv elle2/worm3 elle2/worm2
    ls elle2
    > worm  worm2
  ```
</details>

### ***E. DELETE（permanently）***
The command for delete is `rm`, refers to remove a file. 
```bash
rm elle2/worm3
ls elle2
> worm
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

### ***G. Wildcards***
In Unix/Linux, **wildcards** are special characters that help you work with multiple files and directories at once. They are particularly useful for selecting groups of files without having to list them individually. This can be very handy when you want to manage a large number of files efficiently.

Wildcards include characters like `*`, `?`, and `[]` which allow you to perform operations on files that match certain patterns.

The `*` wildcard matches zero or more characters in a filename. It’s very versatile and is often used to handle files that share common naming patterns.
```
ls *.txt  # Lists all files with a .txt extension
```
The `?` wildcard matches exactly one character.
```
ls worms/worm?
> worms/worm1  worms/worm2  worms/worm3
```
The square brackets [] allow you to specify a range or a set of characters to match.
```
ls worms/worm[2-3]
> worms/worm2  worms/worm3
```

Wildcards can be used with `mv`, `cp`, `rm` and other command as well.


<br><br>
___
   Now you should be able to do the basic operation . Try completing the following exercises:

   - [x] List the files in `/home/shared/aoifolution_exercises`
   - [x] List the `.fasta` files in `/home/shared/aoifolution_exercises`
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
   ls /home/shared/aoifolution_exercises/*.fasta
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
> This worm is cool
cat worms/worm2
> This worm is NOT cool
```

`cat` doesn't mean the meow cat :cat2:, but the short for **concatenate**, which use for concatenate files together and print on the screen. Try to use it on worm1 and worm2 
```bash
cat worms/worm1 worms/worm2
> This worm is cool
> This worm is NOT cool
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
   >>NOTE: use `more --help` to read the manual before you apply the command
  
</details>

`Enter` or use arrow keys to rolling up and down. 

`less` perform the same function as `more` to view a big file. Try `less --help` and `less file` to see what is the different

   >NOTE: `less` was created after `more` to achive some function that `more` doesn't have, such as scrolling up. It is also faster and lighter
   >
   >NOTE: `less` open another window to view but `more` directly print on the screen. **`less` is recommended for viewing a file**


___
<br><br>

## **5.Useful tools and advanced Usages**

What makes unix command line powful is the build-in tools and how you combine to use them.

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

### ***B. redirection `>`*** 

Previously we mentioned, for a command line, the command itself is crucial. Then you can add arguments to apply the function on and options/flags to modify the details of the function. Here we introduce **Redirection** `>` to save the output in a file:

```bash
cat worms/worm1 worms/worm2
> This worm is cool
> This worm is NOT cool
```
```bash
cat worms/worm1 worms/worm2 > worms.txt
cat worms.txt
> This worm is cool
> This worm is NOT cool
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

>NOTE: If you use `>>`, the new output will be appended at the end of the original file.

### ***C. Regular Expressions (RegEx)*** 

What does the **Regular Expressions** in `grep` mean? Basically, it is a grammar of patterns used to match character combinations in strings. They are an incredibly powerful tool for searching, matching, and manipulating text. 
Many Unix commands, like `grep`, `sed`, and `awk`, support RegEx for advanced pattern matching.

RegEx allows you to search for text that matches complex patterns rather than simple fixed strings. This is particularly useful when you don't know the exact form of the text you're searching for or when you're working with large datasets.

Considering RegEx is such a big part, I won't talk much about that here. But I recommend https://regex101.com/ to learn and test your RegEx.


### ***D. wc*** 

`wc` stands for **Word Count**, but it does more than just counting words. It can count lines, words, and characters in a file. This is especially useful when dealing with large files and you need to quickly get a sense of their size or contents. Try:

```bash
wc worms/worm1
> 1 4 18 worms/worm1

```
This output shows:
- 1 line
- 4 words
- 18 characters

You can use specific options with wc:

- `-l`: Count lines only.
- `-w`: Count words only.
- `-c`: Count characters only.

### ***E. pipes `|`*** 

If you used _**R**_, you might be familiar with the pipe function. It combines multiple command together, and use pipe `|` to pass the output of the last command as the input of the next.

For example, you want to know how many worms there are:
```bash
ls worms | wc -l
> 2
```
This is the most common way to count how many files in a directory. It firstly list all the files by `ls` command, and use pipe `|` to pass to the next, then use `wc -l` to count how many files.

So, there are 2 worms in the `worms` folder. 

When I say multiple command, it means you can use pipe `|` to link command til forever. What does this command want to find? 

`grep "homeobox" Homo_sapiens.GRCh38.112.ensembl.gff3 | grep "protein_coding" | grep "^19" | grep "+" | wc -l`

<details>
  <summary>the answers</summary>
   
  This command wants to find in human, how many protein coding homeobox genes on chromsome 19 positive strand.
</details>

**`ls`/`grep` and  `| wc -l` is the most frequent used command. It can help you quickly to know the numbers of files or the numbers of the target you want to know in the folder.**

### ***F. history*** 
Simply type this and see what happpens:
```bash
history
```
You can see a list of the commands that you’ve executed in your current terminal session. This is useful for recalling past commands without retyping them, or for scripting a series of commands.

You can also limit the number of commands shown by history:
```bash
history 10  # Shows the last 10 commands
```
You can re-run a command from your history by referencing its command number:
```bash
!45  # Re-run command number 45
```
Use pipe `|` and other command to search your history:
```bash
history | grep "worm"
```

### ***G. alias*** 

If you need to use a command line a thousand times (for me it is `ls -l`), it is annoying to type it everytime. `alias` allows you to create shortcuts for long or frequently used commands. This is particularly useful when you have a command with many options that you use repeatedly.

```bash
alias ll="ls -l"
```
Now, instead of typing `ls -l` every time, you can simply type `ll`.

```bash
ll
``
However, now try to logout Aoifolution and login and try `ll` agian.
>TIPS: you can logout Aoifolution by press `ctrl` + `d`. If you press them again you can exit the terminal. 
```bash
> ll: command not found
```
This is becasue the alias will disappear after you logout. You can make these aliases permanent by adding them to your `.bashrc`. `.bashrc` is like a configuration file that loaded everytime you login the server. Simply use this command to make this alias permanent:
```bash
echo 'alias ll="ls -l"' >> ~/.bashrc
```
Now you can try to logout Aoifolution and login and try `ll` agian.

### ***H. echo*** 

The `echo` command that we used in last section is very like `print` function in other programming language. `echo` command is used to print text or variables to the terminal. It's often used in scripts to display messages or to output the value of variables.

```bash
echo "Hello, World!" # this would be the first command you learn if you learn from others, but here we teach something actually useful
echo $HOME  # displays your home directory
echo "This worm is also cool" > worms/worm3 # you can use `echo` to write to a file too.
```

>NOTE: the capital words with $ symbol is called **Environment Variables**. They are key-value pairs used by the operating system to configure and control the behavior of processes and applications. They are accessible to all programs in a session and can store system settings, user preferences, or paths.
>
>some command environment variables are $PATH, $HOME, $USER, $PWD.... Try to print them on the screen and guess what are they stand for.

### ***I. sed*** 
When you not only need to search something with `grep` but also want to replace them, you can use the stream editor `sed`. 

`sed` is a powerful stream editor in Unix/Linux used for parsing and transforming text. It reads input, processes it according to provided instructions, and outputs the result. `sed` is often used for tasks like searching, replacing, deleting, or inserting text in files or streams. It is just like the "string" package in R.

The basic function is search and replace: 
```bash
sed 's/search_pattern/replacement/g' file.txt
```
Here, `s` means this is a **Substitute** command and `g` is **Global**, meaning it will replace all occurrences in each line, not just the first.

Lets try to replace all worms in `worms.txt` into elle and save it to `elle.txt` :
```bash
sed 's/worm/elle/g' worms.txt > elle.txt
cat elle.txt
> This elle is cool
> This elle is NOT cool
```

However, it doen't change the orginal file:
```sed
cat worms.txt
> This worm is cool
> This worm is NOT cool
```

**To turn elle into worm permanently**, you can use `-i` option to edit on the orginal file:

```bash
sed 's/elle/worm/g' -i  elle.txt
cat elle.txt
> This worm is cool
> This worm is NOT cool
```

`sed` allows you do more with different options, such as delete lines others. Check its help page to see more.

### ***J. find*** 

`find` is a command used to search for files and directories within a directory hierarchy based on different criteria such as name, size, type, or modification time. 

For example, you want to search a file named `worms.txt` in the current directory:
```bash
find . -name "worms.txt"
> ./worms.txt
```
Or you want to find all `.txt` files `f` or directories `d`.

```bash
find . -name "*.txt"  # Find all .txt files
> ./elle.txt
> ./worm_operation.txt
> ./worms.txt
find . -type d -name "worms"  # Find directories with specific name
> ./worms
```
`find` works well with larger datasets, and you can search by size, time or others. It also works with pipes to execute other command. Check its help page to see more.

___
**These tools—`grep`, `wc`, `history`, `alias`, `sed`, `find` and `echo`—are fundamental utilities in Unix systems. They allow you to search for patterns, count elements in files, manage your command history, create command shortcuts, and display or manipulate text in the terminal.**
___
<br><br>

   Now you should know these fundamental utilities of unix. Try completing the following exercises:

   - [x] cp the human gene `.fasta` file to your home directory
   - [x] use `more` or `less` to view the .fasta file
   - [x] show the first 6 rows of it on the screen
   - [x] show the last 8 rows of it on the screen
   - [x] What is the first gene in the `.fasta` file? Try to find its infomation in the `.gff3` file
   - [x] As we know every gene ID start with `>` in the fasta file, find out how many genes in human genome
   - [x] Write these IDs in a file called "gene_ID.txt"
   - [x] print the last 100 history and write those about worms into a file called "worm_operation.txt"
   - [x] replace `worm` string in that file into `elle` in place
   - [x] logout Aoifolution 
   - [x] alter the command in the answer to add a shortcut of `ssh` command permanently in your environment

<details>
  <summary>click to see the answers</summary>
   
  ```bash
   cp /home/shared/aoifolution_exercises/Homo_sapiens.GRCh38.112.ensembl.fasta
   more Homo_sapiens.GRCh38.112.ensembl.fasta # or less Homo_sapiens.GRCh38.112.ensembl.fasta
   head -6 Homo_sapiens.GRCh38.112.ensembl.fasta # head Homo_sapiens.GRCh38.112.ensembl.fasta -n 6
   tail -8 Homo_sapiens.GRCh38.112.ensembl.fasta # tail Homo_sapiens.GRCh38.112.ensembl.fasta -n 8
   grep "ENSP00000064571" Homo_sapiens.GRCh38.112.ensembl.gff3
   grep ">" Homo_sapiens.GRCh38.112.ensembl.fasta | wc -l
   grep ">" Homo_sapiens.GRCh38.112.ensembl.fasta > gene_ID.txt
   history 100 | grep "worm" > worm_operation.txt
   sed sed 's/worm/elle/g' -i worm_operation.txt
   ctrl + d
   echo 'alias sh="ssh <username>@aoifolution.gen.tcd.ie"' >> ~/.bashrc  # this is useful. Everytime to login the server, just type `sh`
  ```
  
</details>

<br><br>

___
## **6. Jobs**

> You don't have to do this part if you don't have a long-running process to do yet.

When working on a high-performance computing (HPC) system like Aoifolution, it's common to run long-running tasks or background processes. In Unix/Linux, these tasks are called jobs. You can run, manage, and control these jobs easily using several commands. Run this script to see:

```bash
cp /home/shared/aoifolution_exercises/nap.sh # copy the script to your home dirctory
bash nap.sh # run the .sh script with bash
```
**Then count to 10 in your heart.**

### ***A. Running Jobs in the Background `&`*** 
Normally, when you run a command in the terminal, it blocks the terminal until the command completes (so you can do nothing until I finish my napping.). If you want to keep using the terminal while a process runs, you can run the command in the background by use the `&` symbol after the command:

>before that, lets make the nap longer. Do you remeber how to use the text editor to change the content of a file?
> ```bash
> nano nap.sh # then change the number from 10 to 100
> ```

```bash
bash nap.sh &
> [1] 962640
```

### ***B. Check Active Jobs `jobs`*** 
If you want to see which jobs are currently running in the background, use the `jobs` command. This command lists all background jobs associated with the current terminal session.
```bash
jobs
> [1]+  Running                 bash nap.sh &
```
Each job is assigned a job number, such as [1] in the above example, which you can use to control the job.

### ***C. Bringing Jobs to the Foreground `fg`*** 
Sometimes you may want to bring a background job back to the foreground to interact with it or terminate it manually. You can use the `fg` command followed by the job number:
```bash
fg %1  # Bring job 1 to the foreground
```
If you don’t specify a job number, fg will bring the most recent job to the foreground.

### ***D. Suspending and Resuming Jobs `bg`*** 
You can suspend a running job using **Ctrl + Z**. This pauses the job and frees up the terminal for other tasks. The suspended job can be resumed either in the background or foreground.

```bash
bash nap.sh #run a job
^Z # ctrl +z to pasues the job
> [1]+  Stopped                 bash nap.sh
bg %1 # Use the `bg` command to resume the job in the background.
fg %1 # Use the `fg` to bring the job back to the foreground:
```
>TIPS: this is a very useful combination. Sometimes you want to have a trial run on your script first to see if it works, then pause it and put it to backgroud.

### ***E. Killing a Job `kill`*** 

If you want to terminate a background job, you can use the `kill` command followed by the job number or process ID (PID).

```bash
kill %1  # Kill job 1
```

### ***F. Monitoring Jobs and Processes `htop`*** 
`htop` is a more powerful, interactive process viewer for Unix systems. It  offers a more user-friendly, graphical interface to monitor system resources such as CPU, memory, and running processes. We have `htop` installed on Aoifolution so simply type it to launch it:
```bash
htop
```
<br><br><br>
---
https://cmdchallenge.com/
