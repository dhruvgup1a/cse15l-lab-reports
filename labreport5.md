# Lab Report 5

## Part 1 - Debugging Scenario

### Original Post from a Student

Dear Teaching Staff,

I am currently trying to complete the practice skill demo 4 and I am confused with why the `ListExamples.java` file isn't passing all of the `test.sh` test cases. My best guess is that for the first test case, there is an operation that isn't completing because the JUnit test timed out. For the second test case, I am guessing that there is some logic error with how I add the values to the final list but I don't know how to fix it. Additionally, I am confused on how I can make changes to the file without having direct access to it. Can you please provide me with some direction on how to complete this step? 
![Image](lab5pic1.png) 


### A Response from a TA

Sure! First of all, I would reccomend that you do some research on the `vim` command as it is a very useful command that allows users to handle bugs without having direct file access. When it comes to the symptoms you are experiencing in `testMerge`, I would suggest thinking about what would cause a program to time out. Generally, infinite loops are the most common cause of `TimeoutException`. So I would suggest looking at all of loop conditions and making sure that they have the appropriate terminate condition. Looking at the line number listed in the failure message can help (Should be visible in the line `at app//ListExamples.merge(ListExamples.java:42)`). 

For the symptoms in `testFilter`, I would reccomend drawing out what exactly is happening in the code. It appears that the data is getting entered in the wrong order so I would reccomend double checking the `add` method. 

## Part 2 - Reflection

