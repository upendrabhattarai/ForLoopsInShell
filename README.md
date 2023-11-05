# For Loops in the Shell

## Objectives

- To describe the concept of Loops.

  
- To automate a task by using a for loop in a shell.
  <details>
    <summary>•</summary>
    To demonstrate the fundamentals and encourage you all to explore more.
  
  </details>

Loops are a programming construct that allows us to execute a block of code repeatedly over multiple items. Most languages have the concept of loops and they help us to automate repetitive tasks so that we don't have to type in the code multiple times.

---

## Syntax of For loop

```bash
for <variable> in <list>
    do
        <block of code>
done
```

The syntax of the `for loop` follows a structured flow statement. The texts in bold form the backbone of the `for loop` construct and remain constant, no matter, how big or complex your loop is. You need to have these keywords: `for`, `in`, `do`, and `done` in this order. Other texts that go in between change depending on what you want your loop to do. The `<variable>` is a name that will be used to represent each item in the `<list>`. The `<list>` can be a list of numbers, strings, or files. The `<block of code>` is the set of codes you want to execute for each item in the `<list>`.

---

## How do loops work?
Let's work through an example to see what goes through in a loop command.

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

Here our variable is called `numbers` and items in the list represented by the `numbers` variable are `1 2 3 4`. Our block of code contains `echo $numbers` which basically prints out each item in the `numbers` variable. 
In this example, we have this for loop written in multiple lines with some indentation for readability however it can also be written in a single line or without indentation. You might notice that when you start for loop and press enter after the first line, the second line starts `>` sign rather than the regular command prompt `$`. This simply means that the shell is awaiting further commands to complete it. 

---
## Examples
Let's create some files using for loop. We can use `touch` command to create empty files.

```bash
for files in 1.txt 2.txt 3.txt 
do
    touch $files
done
```
You can type `ls` to display the output of the above `for loop`.


## Using multiple commands with the for loop

We can also use multiple commands inside the loop. So in the examples above, we used `echo` and `touch` commands separately in two different for loops. Let's use them together to write some file with text inside them.

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






