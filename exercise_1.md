Scene_1:
You are a PI. and you have 5 students in your lab.
You want to set up folder for each of your five students: `Mandy, Oskar, Jeff, Allison, Eunji` that you can share (e.g. with Dropbox/googledrive) with them and create a text file to keep notes of every meeting with them.
You should first `cd` to your dropbox folder and create everything in there. write a for loop to automate the task.

```
for students in Mandy Oskar Jeff Allison Eunji
do
mkdir ${students}
touch ${students}/Meeting_Notes.txt
done
```
Now you want to send a message to everyone on the meeting day to put their agendas on the file.
```
for students in Mandy Oskar Jeff Allison Eunji
do
echo "$(date) \n Hey ${students}! how are you doing today? \n Please put on your agendas for today's meeting below. \n 1. ...\n 2. ...\n 3. ...\n ..." >>${students}/meeting_notes.txt
done
```

