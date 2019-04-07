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

1. **Individully:** If you haven't already done this in a previous exercise, setup your Git username 
   and email on Nike by modifiying and executing the commands below. 
   When setting the `user.name` property, please provide your name as it appears on eLC and
   Athena. If you have a preferred name, then you may include it in parentheses. For the
   `user.email` property, please use your `@uga.edu` email address:

   ```
   $ git config --global user.name "Mona Lisa (Liz)"
   $ git config --global user.email "email@uga.edu"
   ```
   
   You can verify that these properties were setup correctly by observing the output of
   the following commands:
   
   ```
   $ git config --global user.name
   $ git config --global user.email
   ```

<hr/>

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
   able to see the updated exercise files in their local copies! Furthermore    

1. **EVERYONE:** View the condensed, graphical version of your Git log using `git adog`.
   If you do not have `git adog` alias setup, then enable it using the following
   caommand:
   
   ```
   $ git config --global alias.adog "log --all --decorate --oneline --graph"
   ```

**CHECKPOINT**

<hr/>

For this next checkpoint, we will have you implement a simple sorting algorithm called
[Bubble Sort](https://en.wikipedia.org/wiki/Bubble_sort). There are many different ways to
explain the execution of this algorithm. We will take the approach of breaking up the
algorithm into two methods, `bubble` and `bubbleSort` that work together to sort an array.

1. **Bubble Algo:** This method takes an array, two valid index positions `lo` and `hi` (both inclusive) 
   within the array such that `lo <= hi` and a `Comparator` that is used to perform comparisions. 
   The method iterates over the array from `lo` to `hi - 1` (inclusive) and swaps adjacent elements
   that are not in order according to the ordering induced by the comparator. Here is the signature
   for the method:
   
   ```java
   public static <T> void bubble(T[] array, int lo, int hi, Comparator<T> c)
   ```
   
   1. Here is an example of before and after calling `bubble(array, 0, 4, Integer::compareTo)`
      on an array with elements `[ 2, 3, 1, 4, 5 ]`:
      
      ```java
      System.out.println(Arrays.toString(array)); // [ 2, 3, 1, 4, 5 ]
      bubble(array, 0, 4, Integer::compareTo);
      System.out.println(Arrays.toString(array)); // [ 2, 1, 3, 4, 5 ]
      ```
      
   1. Here is another example before and after calling `bubble(array, 0, 4, Integer::compareTo)`
      on an array with elements `[ 3, 2, 1, 4, 5 ]` :
      
      ```java
      System.out.println(Arrays.toString(array)); // [ 3, 2, 1, 4, 5 ]
      bubble(array, 0, 4, Integer::compareTo);
      System.out.println(Arrays.toString(array)); // [ 2, 1, 3, 4, 5 ]
      ```
   
   This method gets its name from the idea that a call "bubbles" the bigger values to the right
   of the specified range (i.e., from `lo` to `hi`). After a call to `bubble`, 
   **the largest value in the range is guaranteed to be at index `hi`.**

1. As a group, pick a **DRIVER.**, then the have the **DRIVER** implement the `bubble` method
   in `BubbleSort.java`. You may want to implement a static `swap` method to help you perform
   the adjacent swaps. Be sure to include some code in the `main` method to test the 
   implementation. Once your group is confident that the code compiles and runs correctly,
   have the **DRIVER** stage and commit `BubbleSort.java` to their local repository, then
   push the changes up to the repository on GitHub. Everyone else should pull the changes
   after that.

1. **Bubble Sort Algo**: This method also takes an array, two valid index positions `lo` and `hi` (both inclusive) 
   within the array such that `lo <= hi` and a `Comparator` that is used to perform comparisions.
   The method simply calls `bubble(array, 0, hi)` for all valid `hi` values **in reverse order**
   except for `0`. Here is the signature for the method:

   ```java
   public static <T> void bubbleSort(T[] array, int lo, int hi, Comparator<T> c)
   ```

   To sort an entire array of integers referred to by `array`, for example, you might call:
   
   ```java
   bubbleSort(array, 0, array.length - 1, Integer::compareTo);
   ```
   
   This method gets its name from the fact that uses repeated calls `bubble` in order to sort the array. 
   Visually, the algorithm works by breaking up the array into two subsequences: unsorted and sorted.
   Initially, the unsorted sequence is the entire array and the sorted sequence is empty. After each
   call to `bubble`, we know that the largest value in the range is guaranteed to be at index `hi`.
   
   1. Here is a trace of the algorithm, one row for each call to `bubble`:
   
      | Before              | Call                      | After (Unsorted `/` Sorted) |
      |---------------------|---------------------------|-----------------------------|
      | `[ 5, 4, 2, 3, 1 ]` | `bubble(array, 0, 4, c);` | `[ 4, 2, 3, 1/ 5 ]`         |  
      | `[ 4, 2, 3, 1, 5 ]` | `bubble(array, 0, 3, c);` | `[ 2, 3, 1/ 4, 5 ]`         |
      | `[ 2, 3, 1, 4, 5 ]` | `bubble(array, 0, 2, c);` | `[ 2, 1/ 3, 4, 5 ]`         |
      | `[ 2, 1, 3, 4, 5 ]` | `bubble(array, 0, 1, c);` | `[ 1/ 2, 3, 4, 5 ]`         |
      
   1. Here is an example before and after calling `bubbleSort(array, 0, 4, Integer::compareTo)`
      on an array with elements `[ 5, 4, 2, 3, 1 ]`:
      
      ```java
      System.out.println(Arrays.toString(array)); // [ 5, 4, 2, 3, 1 ]
      bubble(array, 0, 4, Integer::compareTo);
      System.out.println(Arrays.toString(array)); // [ 1, 2, 3, 4, 5 ]
      ```
1. As a group, pick a _new_ **DRIVER.**, then the have the **DRIVER** implement the `bubbleSort` 
   method in `BubbleSort.java`. Be sure to include some code in the `main` method to test the 
   implementation. Once your group is confident that the code compiles and runs correctly,
   have the **DRIVER** stage and commit `BubbleSort.java` to their local repository, then
   push the changes up to the repository on GitHub. Everyone else should pull the changes
   after that.
   
1. View the condensed, graphical version of your Git log using `git adog`.

**CHECKPOINT**

<hr/>


**CHECKPOINT**

<hr/>

[![License: CC BY-NC-ND 4.0](https://img.shields.io/badge/License-CC%20BY--NC--ND%204.0-lightgrey.svg)](http://creativecommons.org/licenses/by-nc-nd/4.0/)

<small>
Copyright &copy; Michael E. Cotterell, Brad Barnes, and the University of Georgia.
This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/4.0/">Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International License</a> to students and the public.
The content and opinions expressed on this Web page do not necessarily reflect the views of nor are they endorsed by the University of Georgia or the University System of Georgia.
</small>
