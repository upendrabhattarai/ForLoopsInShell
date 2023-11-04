# Crash Course on For Loops in the Shell

## Objectives

    - Learn the concept of Loops.
    - Write for loops to execute one or more commands.
    
Loops are a programming construct that allows us to repeat a command or a set of commands for each item in a list. Most languages have the concept of loops and they help us to automate repetitive tasks so that we don't have to type in the code multiple times.

---
## Structure or Syntax of For loop

```bash
for variable in list_of_items
do
    command_1 $variable
    command_2 $variable
    ...
done
```

As we said loops are the programming construct, let's look at how they are constructed. In the above example, text that appears bold: `for`, `in`, `do`, and `done` form the backbone of the for loop. They remain constant no matter how big or complex your loop construct might be. For loop always start with `for` command then you need to define a variable name, then comes `in` followed by a list of elements in that variable. After that comes `do` and then comes your command, whatever command you want to iterate over those items/elements in that variable. When you input your complete command you have to type done so that the for loop understands that you are done with your command so it will execute the commands. So there are basically three steps here, first you define a variable with for and in command, then comes your command block starting with do, and finally with done you have to tell the shell that you are done with the loop.

## How do loops work?
Let's work through an example to see what goes through in a loop command.
For example:
Let's take a variable called `numbers` and items in this `numbers` variable are `1 2 3 4`. What we want to do is to display each item in the numbers variable on our screen. We can use the `echo` command.

```bash
for numbers in 1 2 3 4
do
    echo $numbers
done
```

|Loop component                    | Value  |
|----------------------------------|--------|
|variable_name                     | number |
|list                              | 1 2 3 4|
|body (command(s) to be executed)  | echo   |


Let's create some files using for loop. We can use `touch` command to create empty files.

```bash
for files in 1.txt 2.txt 3.txt 
do
    touch $files
done
```

We can use multiple commands inside the loop. So in the examples above, we used `echo` and `touch` commands separately in two different for loops. Let's use them together to write some file with text inside them.

```bash
for files in file-1.txt file-2.txt file-3.txt
do
    touch $files
    echo This is a textfile $files > $files
done
```


```bash
for file in 1.fasta 2.fasta 3.fasta
do
touch $file
echo ">Sequence1
ACGTAGCTAGCTAGCTAGCTAGCT
>Sequence2
GCTAGCTAGCTAGCTAGCTAGCTAGCTAGC
>Sequence3
TAGCTAGCTAGCTAGCTAGCTA" > $file
done
```

```bash
for file in *.fasta
do
    echo $file
    wc -l $file
done
```


If we want to repeat a task 10/20 times, we don't want to have to type in the code 10/20 times, with maybe a slight change each time.


For example, if we need to run a set of commands for multiple files As such they can automate the process

  
---

## Why learn to use the command line?

<details>
  <summary> Greater control</summary>

While the Graphical user interface (GUI) of an operating system (OS) offers a user-friendly and visually appealing experience, the command line provides a way to access the system's backend. This grants you the ability to perform tasks that may not be readily achievable through the GUI. For instance, when encountering computer issues, the command line can be a valuable tool for checking error logs and running diagnostic tools. It also allows you to manage permissions, and user access, and execute complex tasks that might only be possible via the command line.



</details>

<details>
  <summary> Speed and Efficiency</summary>
  
Despite its steep learning curve, the command line offers efficient and quick ways to navigate your system. For example, when dealing with hundreds or thousands of files that require processing through a pipeline, manually handling them through a GUI could take hours or even days. In contrast, the command line allows you to automate these repetitive tasks, reducing the likelihood of errors. You can also create aliases for frequently used commands to enhance speed and efficiency. This eliminates the need to switch back and forth between the mouse and keyboard, making command line work significantly more efficient in many respects.

</details>



<details>
  <summary> Access remote servers</summary>

When working with large datasets, such as high-throughput sequencing data, there are instances where your local PC may not have the processing capacity to handle the millions of sequencing reads effectively. In such situations, you often need to access high-performance computing clusters for enhanced computing power. This can be achieved through the command-line interface, allowing you to connect to remote servers and leverage their computational resources.
    
</details>






