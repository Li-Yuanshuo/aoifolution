# A Beginner's Guide for Aoifolution

Children today have an entirely different way of interacting with electronic devices. Most of them own a smartphone, tablet, or even a VR device earlier than they get a laptop. To them, it feels more intuitive to swipe and tap on a touchscreen than to use other input methods. 

However, in the past, keyboards were the primary way to interact with electronic devices (preceded by teletype machines and punch cards). Even the mouse only became widespread after the advent of graphical user interfaces (GUI). 

So, you might find **command-line** operating systems unfamiliar, but that's perfectly fine—everyone has a beginning.

But first,
## Why is the **command-line tool** used in bioinformatics?

After getting used to modern smart devices, going back to using a keyboard for input might seem primitive. But why do we still do it? 

While many bioinformatics tools provide **graphical user interfaces (GUIs)** (such as MEGA and Geneious), making them more user-friendly for researchers, these tools, along with the hardware they run on (your personal computer), can become very limited when processing large datasets. 
The same computation that might take years on your local computer can be completed in hours on a **high-performance computing (HPC)** system like Aoifolution. 

Most HPC systems operate on **Linux/Unix environments**, where **command-line interfaces (CLIs)** are the standard mode of interaction. This method offers several advantages:


**1. Efficiency and Flexibility**
   
The command line allows you to precisely control complex settings in bioinformatics software through various parameters, and it enables batch processing via scripting. This is crucial for handling large-scale biological data, such as transcriptomic or genomic analyses. By fully utilizing HPC resources, you can significantly improve your efficiency.

**2. Reproducibility and Compatibility**
   
Reproducibility is a cornerstone of any experiment, meaning that under the same conditions, others should be able to reproduce the same results. The command line provides a simple yet comprehensive way to document bioinformatics analysis protocols, unlike vague GUI instructions like “right-click this icon and select that option.” Moreover, software interfaces can vary across operating systems, but command-line tools are often cross-platform compatible, allowing you to run the same workflows on different systems (Linux, macOS, Windows) without worrying about platform-specific differences.

**3. Development, Maintenance, and Integration**
   
For these reasons, most bioinformatics software is designed for command-line interaction. Designing and maintaining a GUI is more complex, as it requires attention to compatibility and resource usage. Command-line tools, however, allow developers to focus on core functionality. Additionally, they are easier to integrate into scripts, pipelines, and automated processes, making them more versatile for large-scale or repetitive tasks.

## What is **Aoifolution**?

As we said, Aoifolution is a high-performance computing (HPC) system.  Here is its tech-specs: 
- Dell PowerEdge R740, purchased April 2021
- 2 x Intel Xeon Silver 4210R CPU @ 2.40GHz (10 cores, 20 threads)
- 2 x 500 GB SSD 
- 44 TB RAID5 (5 x 12 TB + 1 spare)
- 384 GB RAM
- 20 cores and 40 threads in total

As you can see, Aoifolution is probably 10 times more powerful than your local computer. It is more like a **cluster** of many computers.
