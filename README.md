# For Loops in the Shell

## Objectives

- To describe the concept of Loops.

- To automate a task by using a for loop in a shell.
  
- To demonstrate the fundamentals and encourage you all to explore more.
  

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


## Challenge 1
Using multiple commands in a for loop.
Let's echo the numbers 1-4 as in the above example but delay the execution of each iteration by 1 second.

<details>
    <summary>::::Hint::::</summary>

`sleep` command suspends execution for an interval of time.

usage: sleep [seconds]

eg. `sleep 1` for 1 second delay.

</details>

<details>
    <summary>::::Solution::::</summary>

```bash
for numbers in 1 2 3 4
do
    echo $numbers
    sleep 1
done
```

Note: `variable names` can be anything, you don't have to use `numbers` as a variable name for `1 2 3 4` as in the above two examples. You can replace this variable name: `numbers` with anything, eg: `x` or `i` or any other random letters, words, or even numbers. However, having a meaningful variable name will increase the interpretability of the codes.

</details>


---
## Examples
Let's create some files using for loop. We can use `touch` command to create empty files.

```bash
for numbers in 1 2 3 4             # for numbers in {1..4} does the same job
do
    touch ${numbers}.txt
done
```
You can type `ls` to display the output of the above `for loop`.


## More examples

We can use `echo` command to write a file by redirecting the output to a file. 

```bash
for files in 1.txt 2.txt 3.txt 4.txt
do
    echo This is a textfile $files > $files
done
```
You can use `less` command to read the text file.

## Challenge 2
Rewrite the above loop using wild card `*` to list items for the variable and append a second line `This is created with for loop.`in each text file.

<details>
    <summary>::::Hint::::</summary>
  
wild card `*.txt` can specify all the files: 1.txt 2.txt 3.txt and 4.txt in our working directory.

We can use `>` to direct the output from a command to a file. However, redirecting another output of a command to the same file will overwrite the file. So, in order to add a new output/content in the same file, we can use `>>` so the new content will append at the bottom of the text file.

</details>    

<details>
    <summary>::::Solution::::</summary>
  
```bash
for files in *.txt
do
    echo "This is created with for loop." >> $files
done
```
    
</details>

## Project 1

### Setup
Create 4 fasta files: `file_1.fasta, file_2.fasta, file_3.fasta, file_4.fasta, file_5.fasta and file_6.fasta`
insert the following sequences into each file.

```
>Sequence1
ACGTAGCTAGCTAGCTAGCTAGCTTAGCTAGCTAGAGCTAGCTAGCTGCTAGCT
>Sequence2
GCTAGCTAGCTAGCTAGCTAGCTAGCTAGCAGCTAGCTTAGCTAGGCAGCTAG
>Sequence3
TAGCTAGCTAGCTAGCTAGCTATAGCTAGCTAGCTCTAGCTAGCTAGCTGCT
```

<details>
    <summary>::::Solution::::</summary>

```bash
for files in {1..6}
do
touch file_${files}.fasta
echo ">Sequence1
ACGTAGCTAGCTAGCTAGCTAGCTTAGCTAGCTAGAGCTAGCTAGCTGCTAGCT
>Sequence2
GCTAGCTAGCTAGCTAGCTAGCTAGCTAGCAGCTAGCTTAGCTAGGCAGCTAG
>Sequence3
TAGCTAGCTAGCTAGCTAGCTATAGCTAGCTAGCTCTAGCTAGCTAGCTGCT" > $files
done
```
</details>

Fasta files contain the nucleotide sequences. We do not usually generate these sequences with codes. These are generated by sequencing DNA/RNA from biological samples. Assume that you received these six fasta files from a sequencing core. Using a for loop, count how many sequences are there in each fasta file. 

<details>
    <summary>::::Hint::::</summary>

You can use `grep` command to count the number of sequences. As we know, in fasta file, each sequence has a header that starts with ">" sign (">" in ">Sequence1" ">Sequence2"... above) followed by the actual sequence. we can `grep` and use `-c` flag to count all the occurrences of the">" character at the start of a line. Google the use of grep to count sequences in a fasta file if you are stuck.

</details>

<details>
    <summary>::::Solution::::</summary>
  
```bash
for files in *.fasta
do
    echo $files
    grep -c "^>" $files
done
```
</details>
