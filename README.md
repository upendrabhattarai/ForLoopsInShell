# For Loops in the Shell

## **Objectives**

- Understand the concept of Loops in shell scripting.

- Learn how to automate tasks using `For loop`.
  
- Explore the fundamentals and encourage further exploration.

---

Loops are a powerful programming construct that allows us to execute a block of code repeatedly over a set of items. Most programming languages support loops, and they are essential for automating repetitive tasks, eliminating the need to duplicate code.

---

## **Syntax of For loop**

In shell scripting, a for loop follows a specific structure:
```bash
for <variable> in <list>
    do
        <block of code>
done
```
- The keywords `for`, `in`, `do`, and `done` are essential components of the for loop.
- `<variable` represents each item in the `<list>`/
- `<list>` can be numbers, strings, or files.
- `<block of code>` consists of the commands to be executed for each item in the `<list>`.

---

## How Do Loops Work?
Let's walk through an example:

```bash
for numbers in 1 2 3 4
  do
    echo $numbers
done
```

- `numbers` is the variable.
- The list  includes numbers 1, 2, 3, and 4.
- The block of code prints each number using `echo`.

In this example, we have this for loop written in multiple lines with some indentation for readability, however, it can also be written in a single line or without indentation. You might notice that when you start a For loop and press enter after the first line, the second line starts with the `>` sign instead of the regular command prompt `$` or `%`. This `>` simply means that the shell is awaiting further commands to complete it.

---

*Expanding the block of code with more commands.*

Let's expand the block of code in the above example to execute more commands.
This time we will use the `sleep` command to add 1 second delay in each iteration.

<details>
    <summary>::::sleep command::::</summary>


`sleep` command suspends execution for an interval of time.

usage: sleep [seconds] 

eg. `sleep 1` for 1 second delay.

</details>


```bash
for numbers in {1..4}
  do
    echo $numbers
    sleep 1
done
```

**Note:**
`variable names` can be anything, you don't have to use `numbers` as a variable name for `1 2 3 4` as in the above two examples. You can replace this variable name: `numbers` with anything, eg: `x` or `i` or any other random letters, words, or even numbers. However, having a meaningful variable name will increase the interpretability of the codes.

## Challenge 1

Change the <variable name> in the above loop and see if it works differently. 

---

## Examples
1. Create 50 empty files using the `touch` command.

```bash
touch {1..50}.txt
```

Type `ls` to display the output.

## Challenge 2
Use `touch` with `for loop` to create 50 more text files `{51..100}.txt`

<details>
    <summary>::::Solution::::</summary>

```bash
for numbers in {51..100}
  do
    touch ${numbers}.txt
done
```

</details>


`ls` to display the output from the above `for loop`.


2. Write text to files using the `echo` command.


```bash
for files in *.txt               # using wild card * with .txt points to every file in the directory that ends with .txt
do
    echo "This is a textfile $files" > $files
done
```

You can use the `less` command to read the text file.

---


## **Challenge 2**
Rewrite the loop using the wild card `*` to list items for the variable and append a second line to each text file.

<details>
    <summary>::::Hint::::</summary>
  
wild card `*.txt` can specify all the files: 1.txt 2.txt 3.txt and 4.txt in our working directory.

We can use `>` to direct the output from a command to a file. However, redirecting another output of a command to the same file will overwrite the content of the file. So, in order to add a new output/content in the same file, we can use `>>` so the new content will append at the bottom of the text file.

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

## Project 1:

### Setup
Create six fasta files: `file_1.fasta`, `file_2.fasta`, `file_3.fasta`, `file_4.fasta`, `file_5.fasta` and `file_6.fasta` and insert the following sequences into each file.

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
echo ">Sequence1\nACGTAGCTAGCTAGCTAGCTAGCTTAGCTAGCTAGAGCTAGCTAGCTGCTAGCT\n>Sequence2\nGCTAGCTAGCTAGCTAGCTAGCTAGCTAGCAGCTAGCTTAGCTAGGCAGCTAG\n>Sequence3\nTAGCTAGCTAGCTAGCTAGCTATAGCTAGCTAGCTCTAGCTAGCTAGCTGCT" > $files
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
