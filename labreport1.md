# Lab Report 1

## Command: `cd` (Change Directory) 

1. No arguments
   ```
   [user@sahara ~]$ cd
   [user@sahara ~]$ 
   ```
   Working Directory: -
   - The `cd` command is responsible for changing directories and since we had no argument, the directory reset. This resulted in no errors since the default action of this command when no argument is passed is to reset the directory to `-`. 
   
   ---
2. Path to a directory as an argument
   ```
   [user@sahara ~]$ cd lecture1
   [user@sahara ~/lecture1]$ 
   ```
   Working Directory: -
   - In this example, the `cd` command set the directory to be the `lecture1` folder. This resulted in no errors since there is a directory within the working directory called `lecture1`. 
   
   ---
3. Path to a file as an argument
   ```
   [user@sahara ~/lecture1]$ cd Hello.java
   bash: cd: Hello.java: Not a directory
   [user@sahara ~/lecture1]$ 
   ```
   Working Directory: -/lecture1
   - In this example, the `cd` command was trying to set the directory to a file. However, this is not possible since a directory has to be a folder, which resulted in this producing an error. 

## Command: `ls` (List Files) 

1. No arguments
   ```
   [user@sahara ~]$ ls
   lecture1
   [user@sahara ~]$ 
   ```
   Working Directory: -
   - The `ls` command lists all of the files in the current directory. Hence, this example listed all of the files and folders in the working directory, which was just the folder `lecture1`. This produced no errors since the default action of this command is to list the contents of its working directory when no arguments are passed. 

   ---
2. Path to a directory as an argument
   ```
   [user@sahara ~]$ ls lecture1
   Hello.class  Hello.java  messages  README
   [user@sahara ~]$ 
   ```
   Working Directory: -
   - The `ls` command takes a file path to a directory as an argument and lists all of the files in the directory. In this example, it listed all of the files in the `lecture1` folder. This produced no errors since the command was able to detect the directory `lecture1` and list all of the files within it. 
   
   ---
3. Path to a file as an argument
   ```
   [user@sahara ~]$ ls lecture1/Hello.java
   lecture1/Hello.java
   [user@sahara ~]$ 
   ```
   Working Directory: -
   - In this example, since there are no sub files in a file, the terminal outputted the file itself that was in the argument. This produced no errors since the command was able to detect a file in the path passed in the argument. However, since the path didn't lead to a directory, it outputted the argument back to us. 

## Command: `cat` (Concatenate) 

1. No arguments
   ```
   [user@sahara ~]$ cat
   ```
   
   (no output)

   Working Directory: -
   - The `cat` command is responsible for outputting the contents of files onto the terminal. Since there was no file in the argument, the terminal outputted nothing. However, an interesting observation is that when you try typing stuff in the terminal after running the command and hit enter again, it outputs what you typed. This resulted in no errors. It appears that the defualt action of the command with no arguments is to output the user input from the terminal. 
   
   ---
3. Path to a directory as an argument
   ```
   [user@sahara ~]$ cat lecture1
   cat: lecture1: Is a directory
   [user@sahara ~]$ 
   ```
   Working Directory: -
   - This example produced an error since the argument was a file path to a directory, not a file. In order for this command to work, it is important to have the argument be a path to a file. 
   
   ---
5. Path to a file as an argument
   ```
   [user@sahara ~]$ cat lecture1/Hello.java
   import java.io.IOException;
   import java.nio.charset.StandardCharsets;
   import java.nio.file.Files;
   import java.nio.file.Path;

   public class Hello {
     public static void main(String[] args) throws IOException {
       String content = Files.readString(Path.of(args[0]), StandardCharsets.UTF_8);    
       System.out.println(content);
     }
   }[user@sahara ~]$ 
   ```
   Working Directory: -
   - This example outputted the contents of the `lecture1/Hello.java` file, as expected from the command. This produced no errors since the argument was a path that led to a file. This resulted in the command to print the contents of that file onto the terminal. 
   

