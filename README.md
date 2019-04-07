# cs1302-ce27 Paired Algorithm Analysis

In this class exercise, students will implement two different algorithms for
sorting an array, then derive the timing functions for those algorithms for
the purposes of completing a set of algorithm analysese at a later time. Code
and notes will be shared between group members via a private Git repository. 

## References and Prerequisites

* [Setting up your own GitHub Account](https://github.com/cs1302uga/cs1302-tutorials/blob/master/github-setup.md)
* [CSCI 1302 Algorithm Analysis Tutorial](https://github.com/cs1302uga/cs1302-tutorials/blob/master/algo-analysis.md)

## Questions

In your notes, clearly answer the following questions. These instructions assume that you are 
logged into the Nike server. 

**NOTE:** If a step requires you to enter in a command, please provide in your notes the full 
command that you typed to make the related action happen. If context is necessary (e.g., the 
command depends on your present working directory), then please note that context as well.

### Getting Started

1. **You need to be in a group with at least two people for this exercise.**
   We reccommend keeping the groups small. Some steps in this exercise need be
   done by each group member individually.
   
1. **Indivually:** Make sure that you have done the following:

   1. [Setup your Free GitHub Pro Account](https://github.com/cs1302uga/cs1302-tutorials/blob/master/github-setup.md#setting-up-an-account)
   
   1. [Setup your SSH Keys on Nike and GitHub](https://github.com/cs1302uga/cs1302-tutorials/blob/master/github-setup.md#setting-up-ssh-keys)

## Exercise Steps

1. Once each group member has completed the Getting Started steps, 
   pick an ordering for the group members (e.g., Group Member 1, Group Member 2, etc.).
   If a step is being performed by one group member, then everyone is expected
   to watch, pay attention, and take notes.

1. **GROUP MEMBER 1:** Create a [new repository](https://github.com/new) on GitHub with 
   the following information:
   
   | **Field**            | **Value**                                                        |
   |----------------------|------------------------------------------------------------------|
   | **Owner**            | _your account_                                                   |
   | **Repository Name**  | `cs1302-ce27`                                                    |
   | **Description**      | `Repository for Class Exercise 27`                               |
   | **Public / Private** | Private -- You choose who can see and commit to this repository. |
   
   Do **NOT** "Initialize this repository with a README". 
   Also, do **NOT** click on the dropdowns for a `.gitignore` or license file.
   
   Once complete, you should have a GitHub-hosted private Git repository at the following
   website URL: `https://github.com/your_username/cs1302-ce27` where `your_username` is
   your GitHub account username. 
   
   Do **NOT** follow any of the setup instructions at this time.
   
1. **GROUP MEMBER 1:** On the repository's website, add your group members as collaborators
   by going to "Settings" → "Collaborators". This will send them an invite that they can
   accept either via email or by visiting the repository's website on GitHub.
   
1. **OTHER GROUP MEMBERS:** Go to the repository website on GitHub and accept the invition
   from Group Member 1. If you see a 404 error instead of an invitation, then double check
   the following:
   
   * Repository Website URL
   
   * Username that Group Member 1 used when they added you
   
   Before continuing, make sure each group member has access to the repository website.
  
1. **GROUP MEMBER 2:** On Nike, use Maven to create a project directory for this exercise 
   called `cs1302-ce27` with a primary package called `cs1302.ce27`, then do the change
   into that directory and do the following:
   
   1. Delete the Maven-generated driverand the unit test files:
   
      ```
      $ rm -f src/main/java/cs1302/ce27/App.java
      $ rm -rf src/main/test
      ```
   
   1. Initialize a new local Git repository:
      
      ```
      $ git init
      ```
      
   1. Create a [`.gitignore`](https://git-scm.com/docs/gitignore) (hidden file) with the following contents:
   
      ```
      bin/
      doc/
      target/
      *.class
      hs_err_pid*
      *~
      \#*\#
      core.*
      ```
      
      Add and commit the `.gitignore` file to the local repository.
      
   1. Update the POM so that the project works with Java 8. After that, add and commit the `pom.xml` file to 
      the local repository.
      
   1. Create blank source code files for the remaining checkpoints:
   
      ```
      $ touch src/main/java/cs1302/ce27/BubbleSort.java
      $ touch src/main/java/cs1302/ce27/SelectionSort.java
      ```

      Add and commit `src` to the local repository.

   1. Before proceeding, ensure that all tracked files are committed. 

   1. Visit the repository website on GitHub and copy the "SSH" URL under "Quick setup",
      then follow these instructions on Nike to link your local repository to the one on GitHub:
      
      ```
      $ git remote add origin git@github.com:group_member_one/cs1302-ce27.git
      $ git push -u origin master
      ```
      
      If successful, everyone should now be able to see the exercise files on the
      repository website on GitHub!

1. **OTHER GROUP MEMBERS:** Visit the repository website on GitHub and copy the "SSH"
   URL from the green "Clone or download" button, then these instructions on Nike to 
   clone the GitHub-hosted Git repostory on your Nike account:
   
   ```
   $ git clone git@github.com:group_member_one/cs1302-ce27.git
   ```
   
   Change into the directory and confirm that everything is there! You can verify that
   the origin of the `clone` operation is the repository instance on GitHub by
   using the following command:
   
   ```
   $ git remote -v
   ```
   
1. **NEXT GROUP MEMBER:** On Nike, write out the basic skeleton code for a driver class
   in `BubbleSort.java` (we'll write the algorithm in there later), ensuring that the 
   package statement is correct and the file compiles and runs using Maven. Then, stage
   and commit the change to your local repository.
   
   Everyone should notice that although you comitted this to your local copy of the
   repository, the change is not automatically refelected in the other local copies
   nor the copy hosted on GitHub. To send this change to GitHub, use the following 
   command to push:
   
   ```
   $ git push origin master
   ```
   
   If successful, everyone should now be able to see the updated exercise files on the
   repository website on GitHub! However, 
   **they will not see the change reflected in their local copy.** 

1. **OTHER GROUP MEMBERS:** Update your local copy of the repository with the latest
   changes from the repository hosed on GitHub using the following command:
   
   ```
   $ git pull origin master
   ```
   
   If successful, everyone should now be able to see the updated exercise files in
   their local copies!

1. **NEXT GROUP MEMBER:** On Nike, write out the basic skeleton code for a driver class
   in `SelectionSort.java` (we'll write the algorithm in there later), ensuring that the 
   package statement is correct and the file compiles and runs using Maven. Then, stage
   and commit the change to your local repository **and push those changes to GitHub**.
   
1. **OTHER GROUP MEMBERS:** Update your local copy of the repository with the latest
   changes from the repository hosed on GitHub. If successful, everyone should now be 
   able to see the updated exercise files in their local copies!   

**CHECKPOINT**

   

Using Maven, create a project directory for this exercise called `cs1302-ce25` with a primary 
   package called `cs1302.ce25`.

1. Change into the `cs1302-ce25` directory that you just created using Maven, then do the
   following:
   
   1. Initialize a new Git repository:
      
      ```
      $ git init
      ```
      
   1. Create a [`.gitignore`](https://git-scm.com/docs/gitignore) (hidden file) with the following contents:
   
      ```
      bin/
      doc/
      target/
      *.class
      hs_err_pid*
      *~
      \#*\#
      core.*
      ```
      
      Add and commit the `.gitignore` file to the repository.
      
   1. Update the POM so that the project works with Java 8. After that, add and commit the `pom.xml` file to 
      the repository.
   
   1. Delete the Maven-generated driver (i.e., `src/main/java/cs1302/ce25/App.java`) and the unit test files 
      (i.e., everything under `src/test/java`). We won't add the `src` folder to the repository at this time
      because it only contains empty subdirectories. Git will not track empty directories.
   
## Exercise Steps

1. For this checkpoint, you will implement your own version of the Unix `find` command.
   Here is an example:
   
   ```
   $ find src
   ```
   
   ```
   src
   src/main
   src/main/java
   src/main/java/cs1302
   src/main/java/cs1302/ce25
   src/main/java/cs1302/ce25/Find.java
   ```
   
1. Create a `cs1302.ce25.Find` class based on code below that provides some
   starter code for your recursive implementation of the Unix `find` command:

   ```java
   public class Find {
   
       public static void printFile(File file) {
           // TODO implement printFile
       } // printFile
    
       public static void main(String[] args) {
           if (args.length == 0) {
               args = new String[] { "." }; // default to "."
           } // if
           // TODO implement stream code
       } // main

   } // Find
   ```
   
   Before this code will compile, you will need to manually setup the package 
   statement and imports.
    
1. **Next, use Maven to compile and run the code.** You won't see any output at
   this point. Please use the `exec:java` phase to run. To provide command-line
   arguments to your program through maven, you will need to specify the 
   command-line arguments as a space-separated
   string with the `-Dexec.args` option (e.g., `-Dexec.args="src target"`) in 
   addition to providing the `-Dexec.mainClass` option. 
   
   * Once you figure out how to run it, please write down that command
     in your notes.
   
   * After you've confirmed that it compiles and runs, please add and commit
     your changes to the repository.

1. Use a stream to map all of the command-line arguments in the `main` method 
   to new [`File`](https://docs.oracle.com/javase/8/docs/api/java/io/File.html)
   objects, then call `printFile` for-each of them. For testing 
   purposes, you may want to put some kind of print statement in the `printFile` method.
   After verifying that your code compiles and works using Maven, 
   please add and commit `Find.java`.
   
1. Implement the `printFile` method. 

   1. If the file or directory denoted by the `File` object does not exists, then
      print an error similar to the following to standard error where `%s` denotes
      the pathname string for the `File` object:
      
      ```
      find: `%s': No such file or directory
      ```
      
   1. the file or directory denoted by the `File` object does exist, print the 
      pathname string for the `File` objectc to standard output. Additionally,
      if the `File` object refers to a directory, then **use recusion** to do the 
      same for all files in the directory. For this part, you may use a stream or a 
      for-each loop.
      
   After verifying that your code compiles and works using Maven, 
   please stage and commit your changes to the repository.

**CHECKPOINT**

1. For this checkpoint, adapt your `Find.java` code to create a 
   `cs1302.ce25.Tree` class that provides a recursive implementation of the 
   Unix [`Tree`](https://en.wikipedia.org/wiki/Tree_(command)) command. 
   Here is an example:
   
   ```
   $ tree src
   ```
   
   ```
   |---src
   |   |---main
   |   |   |---java
   |   |   |   |---cs1302
   |   |   |   |   |---ce25
   |   |   |   |   |   |---Find.java
   |   |   |   |   |   |---Tree.java
   ```
   
   ```
   $ tree src/main/java
   ```
   
   ```
   |---java
   |   |---cs1302
   |   |   |---ce25
   |   |   |   |---Find.java
   |   |   |   |---Tree.java
   ```
   
   Remember, you can add additional parameters to methods, as needed, to
   help you accomplish a given sub-problem.
   
1. **Next, use Maven to compile and run the code.** Please use the `exec:java` phase to run.
   You will need to specify the command-line arguments as a space-separated
   string with the `-Dexec.args` option (e.g., `-Dexec.args="src"`) in addition
   to providing the `-Dexec.mainClass` option. 
   
   * Once you figure out how to run it, please write down that command
     in your notes.
   
   * After you've confirmed that it compiles and runs, please add and commit
     your changes to the repository.

**CHECKPOINT**

1. For this checkpoint, you will implement a recursive method called `shrinkString`.
   Create a `cs1302.ce25.ShrinkString` class that contains a `main` method as well
   as the following method:
   
   ```java
   public static String shrinkString(String str)
   ```

   Given a string, return recursively a "shrinked" string where adjacent characters 
   that are the same have been reduced to a single character. 
   Here are some examples:

   | Example                   | Result   |
   |---------------------------|----------|
   | `shrinkString("yyzzza")`  | `"yza"`  |
   | `shrinkString("abbbcdd")` | `"abcd"` |
   | `shrinkString("Hello")`   | `"Helo"` |
   | `shrinkString("abcd")`    | `"abcd"` |
   | `shrinkString("  ")`      | `" "`    |
   | `shrinkString("")`        | `""`     |
   
   In the `main` method, create an array of strings that contains the strings used in the
   eamples above. Next, create another method called `printShrunkString` with the
   following signature:
   
   ```java
   public static printShrunkStrings(String[] array, int i)
   ```
   
   Given an `array` and an index `i`, print the result of calling `shrinkString`
   on the element at index `i`, then recursively print the remaining elements. You
   may assume the first call provides a valid index `i`. You may not assume
   the array is non-empty.
   
   In the `main` method, use your `printShrunkString` method to print the result 
   of calling `shrinkString` on each element of the array.
   
1. **Use Maven to compile and run the code.** Please use the `exec:java` phase to run.
   You will need to specify the command-line arguments as a space-separated
   string with the `-Dexec.args` option (e.g., `-Dexec.args="src"`) in addition
   to providing the `-Dexec.mainClass` option. 
   
   * Once you figure out how to run it, please write down that command
     in your notes.
   
   * After you've confirmed that it compiles and runs, please add and commit
     your changes to the repository.

**CHECKPOINT**

<hr/>

[![License: CC BY-NC-ND 4.0](https://img.shields.io/badge/License-CC%20BY--NC--ND%204.0-lightgrey.svg)](http://creativecommons.org/licenses/by-nc-nd/4.0/)

<small>
Copyright &copy; Michael E. Cotterell, Brad Barnes, and the University of Georgia.
This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/4.0/">Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International License</a> to students and the public.
The content and opinions expressed on this Web page do not necessarily reflect the views of nor are they endorsed by the University of Georgia or the University System of Georgia.
</small>
