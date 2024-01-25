# Lab Report 1

## Command: `cd` (Change Directory) 

1. No arguments
   ```
   [user@sahara ~]$ cd
   [user@sahara ~]$ 
   ```
   Working Directory: -
   - The `cd` command is responsible for changing directories and since we had no argument, the directory reset. 
   
   ---
2. Path to a directory as an argument
   ```
   [user@sahara ~]$ cd lecture1
   [user@sahara ~/lecture1]$ 
   ```
   Working Directory: -
   - In this example, the `cd` command set the directory to be the `lecture1` folder. 
   
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
   - The `ls` command lists all of the files in the current directory. Hence, this example listed all of the files and folders in the working directory, which was just the folder `lecture1`. 

   ---
2. Path to a directory as an argument
   ```
   [user@sahara ~]$ ls lecture1
   Hello.class  Hello.java  messages  README
   [user@sahara ~]$ 
   ```
   Working Directory: -
   - The `ls` command takes a file path to a directory as an argument and lists all of the files in the directory. In this example, it listed all of the files in the `lecture1` folder. 
   
   ---
3. Path to a file as an argument
   ```
   [user@sahara ~]$ ls lecture1/Hello.java
   lecture1/Hello.java
   [user@sahara ~]$ 
   ```
   Working Directory: -
   - In this example, since there are no sub files in a file, the terminal outputted the file itself that was in the argument. 

## Command: `cat` (Concatenate) 

1. No arguments
   ```
   [user@sahara ~]$ cat
   ```
   
   (no output)

   Working Directory: -
   - The `cat` command is responsible for outputting the contents of files onto the terminal. Since there was no file in the argument, the terminal outputted nothing. However, an interesting observation is that when you try typing stuff in the terminal after running the command and hit enter again, it outputs what you typed. 
   
   ---
3. Path to a directory as an argument
   ```
   [user@sahara ~]$ cat lecture1
   cat: lecture1: Is a directory
   [user@sahara ~]$ 
   ```
   Working Directory: -
   - This example produced an error since the argument was a file path to a directory, not a file. 
   
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
   - This example outputted the contents of the 'lecture1/Hello.java' file, as expected from the command. 
   

