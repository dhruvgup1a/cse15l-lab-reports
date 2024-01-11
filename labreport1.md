# Lab Report 1

## Command: `cd` (Change Directory) 

1. No arguments
   ```
   [user@sahara ~]$ cd
   [user@sahara ~]$ 
   ```
   ---
2. Path to a directory as an argument
   ```
   [user@sahara ~]$ cd lecture1
   [user@sahara ~/lecture1]$ 
   ```
   ---
3. Path to a file as an argument
   ```
   [user@sahara ~/lecture1]$ cd Hello.java
   bash: cd: Hello.java: Not a directory
   [user@sahara ~/lecture1]$ 
   ```

## Command: `ls` (List Files) 

1. No arguments
   ```
   [user@sahara ~]$ ls
   lecture1
   [user@sahara ~]$ 
   ```
   ---
2. Path to a directory as an argument
   ```
   [user@sahara ~]$ ls lecture1
   Hello.class  Hello.java  messages  README
   [user@sahara ~]$ 
   ```
   ---
3. Path to a file as an argument
   ```
   [user@sahara ~]$ ls lecture1/Hello.java
   lecture1/Hello.java
   [user@sahara ~]$ 
   ```

## Command: `cat` (Concatenate) 

1. No arguments
   ```
   [user@sahara ~]$ cat
   ```
   (no output)
   ---
3. Path to a directory as an argument
   ```
   [user@sahara ~]$ cat lecture1
   cat: lecture1: Is a directory
   [user@sahara ~]$ 
   ```
   ---
4. Path to a file as an argument
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

