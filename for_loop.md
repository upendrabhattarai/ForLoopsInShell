# For Loops in the Shell

## **Objectives**

- Understand the concept of loops in shell scripting.

- Learn how to automate tasks using `for` loops.
  
- Explore the fundamentals and encourage further exploration.

---

Loops are a powerful programming construct that enables us to execute a block of code repeatedly over a set of items. Most programming languages support loops, and they are essential for automating repetitive tasks, eliminating the need to duplicate code.

---

## **Syntax of For loop**

In shell scripting, a `for` loop follows a specific structure:

```bash
for <variable> in <list>
do
  <block of code>
done
```
- The keywords `for`, `in`, `do`, and `done` are essential components of the `for` loop.
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

In this example:
- `numbers` is the variable.
- The list  includes numbers 1, 2, 3, and 4.
- The block of code prints each number using `echo` command.

We have this `for` loop written in multiple lines with some indentation for readability; however, it can also be written in a single line or without indentation. You might notice that when you start a `for` loop and press enter after the first line, the second line starts with the `>` sign instead of the regular command prompt `$` or `%`. This `>` simply means that the shell is awaiting further commands to complete it.

---

**Expanding the block of code with more commands.**

Let's expand the block of code in the above example to execute more commands.
This time we will use the `sleep` command to add 1 second delay for the execution of each iteration.

<details>
    <summary>::::sleep command::::</summary>


The `sleep` command suspends execution for an interval of time.

Usage: `sleep [seconds]`

For example, `sleep 1` for a 1-second delay.

</details>


```bash
for numbers in {1..4}
do
  echo $numbers
  sleep 1
done
```

**Note:**
variable names can be anything; you don't have to use `numbers` as a variable name for `1 2 3 4` as in the above two examples. You can replace this variable name: `numbers` with anything, eg., `x` or `i` or any other random letters, words, or even numbers. However, having a meaningful variable name will increase the interpretability of the codes.


---

## Examples

###1. Create 10 empty files using the `touch` command.

```bash
touch {1..10}.txt
```

Type `ls` to display the output.

### Challenge 1:
Use `touch` with a `for` loop to create 10 more text files `{11..20}.txt`

<details>
    <summary>::::Solution::::</summary>

```bash
for numbers in {11..20}
do
  touch ${numbers}.txt
done
```

</details>


Use `ls` to display the output from the above `for` loop.


### 2. Setting up a scenario-1.
Suppose you are a PI in your lab, and you have 5 new graduate students this year: Allison, Jeff, Sam, Eunji, and Oskar. You want to set up a folder for each of your students to share files between you two. You also want to create a text file `Meeting_notes.txt` inside each of your students' folders to record your meeting agendas and notes. Create a folder `students` on your desktop and prepare the file system inside that using the `for` loop.

Commands you will be using: `mkdir` and `touch`.

<details>
    <summary>::::Hints::::</summary>
  
wild card `*.txt` can specify all files that end with .txt on the working directory.


</details>    

```bash
for students in Allison Jeff Sam Eunji Oskar
do
  mkdir ${students}
  touch ${students}/Meeting_notes.txt
done
```

## Challenge 2:

Now you want to send a note to everyone on the meeting day to put their agendas on the file `Meeting_notes.txt`. Write a `for` loop to do it. Your message could include: `Hi <student name>, I am looking forward to our meeting today. Please put your agendas for today's meeting below.` You can also print the date with `date` command `$(date)`.

<details>
    <summary>::::Hints::::</summary>

`\n` indicates a line break.

$(): Commands inside Dollar single parentheses get executed and you get then output gets placed into whatever string you are building.

${}: The dollar braces is for variable interpolation. You use it when normal string interpolation could get weird.

We can use `>` to direct the output from a command to a file. However, redirecting another output of a command to the same file will overwrite the content of the file. So, in order to append a new output/content in the same file, we can use `>>`.

</details>

<details>
    <summary>::::Solution::::</summary>

```bash
for students in Mandy Oskar Jeff Allison Eunji
do
  echo "$(date)\n Hi ${students}! I am looking forward to our meeting today.\n Please put on your agendas for today's meeting below." >> ${students}/meeting_notes.txt
done
```

</details>


## Setting up a scenario-2:
First, let's create three fasta files with the `touch` command.
`file_1.fasta`, `file_2.fasta`, `file_3.fasta`

```bash
touch file_{1..3}.fasta
```
Now insert the following sequences into each file using the `for` loop. You can use wild card `*` to specify the list of fasta files.

```bash
>Sequence1\nACGTAGCTAGCTAGCTAGCTAGCTTAGCTAGCTAGAGCTAGCTAGCTGCTAGCT\n>Sequence2\nGCTAGCTAGCTAGCTAGCTAGCTAGCTAGCAGCTAGCTTAGCTAGGCAGCTAGA\n>Sequence3\nTAGCTAGCTAGCTAGCTAGCTATAGCTAGCTAGCTCTAGCTAGCTAGCTGCTGT
```

<details>
    <summary>::::Solution::::</summary>

```bash
for files in *.fasta
do
  echo ">Sequence1\nACGTAGCTAGCTAGCTAGCTAGCTTAGCTAGCTAGAGCTAGCTAGCTGCTAGCT\n>Sequence2\nGCTAGCTAGCTAGCTAGCTAGCTAGCTAGCAGCTAGCTTAGCTAGGCAGCTAG\n>Sequence3\nTAGCTAGCTAGCTAGCTAGCTATAGCTAGCTAGCTCTAGCTAGCTAGCTGCT" > $files
done
```
</details>

Fasta file usually contains nucleotide or amino acid sequences. We do not usually generate these sequences with codes. These files are generated through a sequencing machine after sequencing the biological samples. For now, let's assume that we received these three fasta files from a sequencing core. 
Now, using a `for` loop, count how many sequences are there in each fasta file. 

Command you will be using: `grep`

<details>
    <summary>::::Hint::::</summary>

The `grep` command can be used to search a specified pattern in the specified file. As we know each fasta sequence has a header line and each header starts with a `>` sign. we can use `grep` with `-c` option to count the occurrence of `>` at the start of the line to get the number of sequences.

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
