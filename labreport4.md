# Lab Report 3

### Step 4 - Log into ieng6

![Image](lab4step4.png) 

* Keys Pressed: `ssh d1gupta@ieng6.ucsd.edu<enter>`
* `ssh d1gupta@ieng6.ucsd.edu` allows me to create the command to log into ieng6 and `<enter>` runs the command. 

### Step 5 - Clone your fork of the repository from your Github account (using the `SSH` URL)

![Image](lab4step5.png) 

* Keys Pressed: `git clone<ctrl + v><enter>`
* `git clone` allows me to create a clone of an existing repository. Since I had already copied over the github repository link (git@github.com:dhruvgup1a/lab7.git), I simply pasted it into the terminal using the command `<ctrl + v>` and used `<enter>` to run the command. 

### Step 6 - Run the tests, demonstrating that they fail

![Image](lab4step6.png) 

* Keys Pressed: `cd lab7<enter>bash test.sh<enter>`
* `cd lab7` creates the command that allows me to set my directory to `lab7` and `<enter>` runs the command. After that, I use the `bash` command to run the `test.sh` file which containts the test cases I need to run. 

### Step 7 - Edit the code file to fix the failing test

![Image](lab4step7.png) 

* Keys Pressed: `vim<space>L<tab>.java<enter>kkkkkkllllllllllxi2<esc>:wq <enter>`
* `vim L<tab>.java<enter>` allowed me to use the vim command to open a file named `ListExamples.java`, since the `L<tab>` autofills to `ListExamples.java` (final command in terminal was `vim ListExamples.java`). After that I navigated the file from the bottom by getting to the error in the code by pressing `kkkkkkllllllllll`. After that, I removed the character `1` by pressing `x` and inserted the character `2` by pressing `xi2`. I then left the inserting window by pressing `<esc>` and left the vim by pressing `:wq<space><enter>`.
* The error was in the last loop in the method which was changing the `index1` variable instead of the `index2` variable. So the fix the issue, we changed `index1` to `index2` in the loop. 

### Step 8 - Run the tests, demonstrating that they now succeed

![Image](lab4step8.png) 

* Keys Pressed: `<up><up><enter>`
* The command `bash test.sh` was two up in my history so I used the up arrow to access it. 

### Step 9 - Commit and push the resulting change to your Github account

![Image](lab4step9.png) 

* Keys Pressed: `git add<tab><enter>git commit -m "fixed issue"<enter>`
* I pressed `git add<tab><enter>` to stage the file `ListExamples.java` for a commit to the github repository (final command in terminal was `git add ListExamples.java`). After that I ran the `git commit` command with the message `"fixed issue"` in order update the repository on github with a message explaining the updates. 


