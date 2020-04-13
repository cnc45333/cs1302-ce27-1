# cs1302-ce27 Paired Sorting Algorithm Analysis

![Approved for: Fall 2019](https://img.shields.io/badge/Approved%20for-Fall%202019-brightgreen)
<!--![Approved for: Spring 2020](https://img.shields.io/badge/Approved%20for-Spring%202020-blue)
![Instruction: Online](https://img.shields.io/badge/Instruction-Online-important)-->

In this class exercise, students will prepare for the next exercise by ensuring
their GitHub accounts and private repositories are setup correctly. Code
and notes will be shared between group members via a private Git repository. 

## Course-Specific Learning Outcomes
* **LO3.d:** Apply pair-programming principles in a software-based project.
* **LO5.a:** Utilize a version control tool such as Git or Subversion to store and update source 
code in a multi-programmer software solution.
* **LO6.c:** (Partial) Implement, analyze, and assess combinations of searching/sorting 
algorithms such as linear search, binary search, quadratic sorts, and linearithmic sorts.

## References and Prerequisites

* [Setting up your own GitHub Account](https://github.com/cs1302uga/cs1302-tutorials/blob/master/github-setup.md)
* [CSCI 1302 Algorithm Analysis Tutorial](https://github.com/cs1302uga/cs1302-tutorials/blob/master/algo-analysis.md)

## Questions

In your notes, clearly answer the following questions. These instructions assume that you are 
logged into the Nike server. 

**NOTE:** If a step requires you to enter in a command, please provide in your notes the full 
command that you typed to make the related action happen. If context is necessary (e.g., the 
command depends on your present working directory), then please note that context as well.

![Extra Credit](ecop.png)

We will **double the points** that you earn for this exercise if you meet the following criteria:

1. Met with another student in the Spring 2020 CSCI 1302 online (e.g., via Zoom) to complete
   the pair programming aspects of this exercise; and
   
1. Completed all checkpoints.

The Git log in your submitted exercise will help us determine if you met these criteria.

## Getting Started

1. To get the most out of this exercise, we encourage you to
   **form a group of exactly two people for this exercise.**
   
   * **Working in a group?** Some steps in this exercise need be done by each group member individually.
   
   * **Working by yourself?** That's okay. If the instructions ask you to switch, then don't switch.
   
1. **Individually:** Make sure that you have done the following:

   1. [Setup your Free GitHub Pro Account](https://github.com/cs1302uga/cs1302-tutorials/blob/master/github-setup.md#setting-up-an-account)
   
   1. [Setup your SSH Keys on Nike and GitHub](https://github.com/cs1302uga/cs1302-tutorials/blob/master/github-setup.md#setting-up-ssh-keys)

1. **Individually:** If you haven't already done this in a previous exercise, setup your Git username 
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
   
1. For this checkpoint, please be ready to show the public key that you generated on Nike both on
   Nike and on your GitHub account.
   
   * To see the copy of your public key on Nike:
     ```
     $ cat ~/.ssh/id_rsa.pub
     ```
   * To see the copy of your public key on GitHub, please visit: https://github.com/settings/keys
   
## Exercise Steps

### Checkpoint 1 Steps

1. **In a group?**

   * **If yes,** then let's do some **pair programming!** The instructions will refer to Group Member 1 and
     Group Member 2. That means you need to pick an ordering. We recommend that use Comte de Rochambeau's 
     technique to determine who gets to be the driver first, i.e., who gets to be Group Member 1.
   
     > Comte de Rochambeau was a French nobleman who fought against the British during the Revolutionary War.
     > His name served as a codeword at the battle of Yorktown, where he commanded the French troops.
     > Legend has it that Comte de Rochambeau made decisions using a technique known as _roshambo_
     > or _rock, paper, scissors_. 
     > **-- A Legend told by Some Old, Wise Person**
     
   * **If no,** then you will need to follow the instructions for both Group Member 1 and Group Member 2
     in the instructions below. 

1. **GROUP MEMBER 1:** Create a [new repository](https://github.com/new) on GitHub with 
   the following information:
   
   | **Field**            | **Value**                                                        |
   |----------------------|------------------------------------------------------------------|
   | **Owner**            | _your account_                                                   |
   | **Repository Name**  | `cs1302-ce27-ce28`                                                    |
   | **Description**      | `Repository for Class Exercise 27 and 28`                               |
   | **Public / Private** | Private -- You choose who can see and commit to this repository. |
   
   Do **NOT** "Initialize this repository with a README". 
   Also, do **NOT** click on the dropdowns for a `.gitignore` or license file.
   
   Once complete, you should have a GitHub-hosted private Git repository at the following
   website URL: `https://github.com/your_username/cs1302-ce27-ce28` where `your_username` is
   your GitHub account username. 
   
   Do **NOT** follow any of the setup instructions at this time.
   
1. **If not in a group,** skip to the next step; otherwise, perform the sub-steps below.   

   1. **GROUP MEMBER 1:** On the repository's website, add your group members as collaborators
      by going to "Settings" → "Collaborators". This will send them an invite that they can
      accept either via email or by visiting the repository's website on GitHub.
   
   1. **GROUP MEMBER 2:** Go to the repository website on GitHub and accept the invition
      from Group Member 1. If you see a 404 error instead of an invitation, then double check
      the following:
   
      * Repository Website URL
   
      * Username that Group Member 1 used when they added you
   
      Before continuing, make sure each group member has access to the repository website.
  
1. **GROUP MEMBER 2:** On Nike, use Maven to create a project directory for this exercise 
   called `cs1302-ce27-ce28` with a primary package called `cs1302.sorting`, then change
   into that directory and do the following:
   
   1. Delete the Maven-generated driver and the unit test files:
   
      ```
      $ rm -f src/main/java/cs1302/sorting/App.java
      $ rm -rf src/test
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
      
   1. Create blank source code files for future checkpoints:
   
      ```
      $ touch src/main/java/cs1302/sorting/BubbleSort.java
      $ touch src/main/java/cs1302/sorting/SelectionSort.java
      ```

      Add and commit `src` to the local repository.

   1. Before proceeding, ensure that all tracked files pass `checkstyle` and are committed. 

   1. Visit the repository website on GitHub and copy the "SSH" URL (i.e., the `git@github...` URL)
      under "Quick setup", then follow these instructions on Nike to link your local repository 
      to the one on GitHub:
      
      ```
      $ git remote add origin git@github.com:group_member_one/cs1302-ce27-ce28.git
      $ git push -u origin master
      ```
      
      If successful, everyone should now be able to see the exercise files on the
      repository website on GitHub!
   
1. **GROUP MEMBER 1:** On Nike, write out the basic skeleton code for a driver class
   in `BubbleSort.java` (**you do NOT need to implement it now**; we'll write the algorithm 
   in there later), ensuring that the  package statement is correct and the file compiles 
   and runs using Maven. Then, check `checkstyle`, stage, and commit the change to your local repository.
   
   **Please take note:** Although you comitted this to your local copy of the
   repository, the change is not automatically refelected in the  the copy hosted on GitHub. 
   To send this change to GitHub, use the following command to push:
   
   ```
   $ git push origin master
   ```
   
   If successful, everyone should now be able to see the updated exercise files on the
   repository website on GitHub! However, 
   **if you're in a group, then GROUP MEMBER 2 will not see the change reflected in their local copy.** 

1. **GROUP MEMBER 2:** Update your local copy of the repository with the latest
   changes from the repository hosed on GitHub using the following command:
   
   ```
   $ git pull origin master
   ```
   
   If successful, everyone should now be able to see the updated exercise files in
   their local copies!

1. **GROUP MEMBER 2:** On Nike, write out the basic skeleton code for a driver class
   in `SelectionSort.java` (we'll write the algorithm in there later), ensuring that the 
   package statement is correct and the file compiles and runs using Maven. Then, check 
   `checkstyle`, stage, and and commit the change to your local repository with
   message **`"checkpoint-1"`**, then **push those changes to GitHub**.
   
1. **GROUP MEMBER 1:** Update your local copy of the repository with the latest
   changes from the repository hosted on GitHub. If successful, everyone should now be 
   able to see the updated exercise files in their local copies! Furthermore    

1. **EVERYONE:** View the condensed, graphical version of your Git log using `git adog`.

<hr/>

![CP](https://img.shields.io/badge/Just%20Finished%20Checkpoint-1-success?style=for-the-badge)

<hr/>

### Checkpoint 2 Steps

For this next checkpoint, we will have you implement a simple sorting algorithm called
[Bubble Sort](https://en.wikipedia.org/wiki/Bubble_sort). **There are many different ways to
explain the execution of this algorithm.** We will take the approach of breaking up the
algorithm into two methods, `bubble` and `bubbleSort` that work together to sort an array.

**Bubble Algo:** This is a helper algorithm that does not, itself, sort the array. 
This method takes an array, two valid index positions `lo` and `hi` (both inclusive) 
within the array such that `lo <= hi` and a `Comparator` that is used to perform comparisions. 
The method iterates over the array from `lo` to `hi - 1` (inclusive) and **swaps adjacent elements**
that are **not in order** according to the ordering induced by the comparator (i.e., calling 
`c.compare`). Here is the signature for the method:
   
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
      
      Here are is an overview of the internal steps taken in this example:
      
      | `lo` | `hi` | `hi - 1` |
      |------|------|----------|
      | `0`  | `4`  | `3`      |
      
      | Iteration | Before              | `(a, b)` | `c.compare(a, b) > 0` | Action  | After               |
      |-----------|---------------------|----------|-----------------------|---------|---------------------|
      | `0`       | `[(2, 3) 1, 4, 5 ]` | `(2, 3)` | `false`               | no swap | `[ 2, 3, 1, 4, 5 ]` |
      | `1`       | `[ 2 (3, 1) 4, 5 ]` | `(2, 1)` | `true`                | do swap | `[ 2, 1, 3, 4, 5 ]` |
      | `2`       | `[ 2, 1 (3, 4) 5 ]` | `(3, 4)` | `false`               | no swap | `[ 2, 1, 3, 4, 5 ]` |
      | `3`       | `[ 2, 1, 3 (4, 5)]` | `(4, 5)` | `false`               | no swap | `[ 2, 1, 3, 4, 5 ]` |
      
   1. Here is another example before and after calling `bubble(array, 0, 4, Integer::compareTo)`
      on an array with elements `[ 3, 2, 1, 5, 4 ]` :
      
      ```java
      System.out.println(Arrays.toString(array)); // [ 3, 2, 1, 5, 4 ]
      bubble(array, 0, 4, Integer::compareTo);
      System.out.println(Arrays.toString(array)); // [ 2, 1, 3, 4, 5 ]
      ```
      
      Here are is an overview of the internal steps taken in this example:
      
      | `lo` | `hi` | `hi - 1` |
      |------|------|----------|
      | `0`  | `4`  | `3`      |
      
      | Iteration | Before              | `(a, b)` | `c.compare(a, b) > 0` | Action  | After               |
      |-----------|---------------------|----------|-----------------------|---------|---------------------|
      | `0`       | `[(3, 2) 1, 5, 4 ]` | `(3, 2)` | `true`                | do swap | `[ 2, 3, 1, 5, 4 ]` |
      | `1`       | `[ 2 (3, 1) 5, 4 ]` | `(3, 1)` | `true`                | do swap | `[ 2, 1, 3, 5, 4 ]` |
      | `2`       | `[ 2, 1 (3, 5) 4 ]` | `(3, 5)` | `false`               | no swap | `[ 2, 1, 3, 5, 4 ]` |
      | `3`       | `[ 2, 1, 3 (5, 4)]` | `(5, 4)` | `true`                | do swap | `[ 2, 1, 3, 4, 5 ]` |
      
   1. Here is another example before and after calling `bubble(array, 0, 1, Integer::compareTo)`
      on an array with elements `[ 2, 1, 3, 4, 5 ]` :
      
      ```java
      System.out.println(Arrays.toString(array)); // [ 2, 1, 3, 4, 5 ]
      bubble(array, 0, 1, Integer::compareTo);
      System.out.println(Arrays.toString(array)); // [ 1, 2, 3, 4, 5 ]
      ```
      
      Here are is an overview of the internal steps taken in this example:
      
      | `lo` | `hi` | `hi - 1` |
      |------|------|----------|
      | `0`  | `1`  | `0`      |
      
      | Iteration | Before              | `(a, b)` | `c.compare(a, b) > 0` | Action  | After               |
      |-----------|---------------------|----------|-----------------------|---------|---------------------|
      | `0`       | `[(2, 1) 3, 4, 5 ]` | `(2, 1)` | `true`                | do swap | `[ 1, 2, 3, 4, 5 ]` |
   
This method gets its name from the idea that a call "bubbles" the bigger values to the right
of the specified range (i.e., from `lo` to `hi`). After a call to `bubble`, 
**the largest value in the range is guaranteed to be at index `hi`.**

1. **GROUP MEMBER 1:** Implement the `bubble` method
   in `BubbleSort.java`. You may want to implement a static `swap` method to help you perform
   the adjacent swaps. 
   
1. **GROUP MEMBER 1:** Write some code in the `main` method to test the implementation of `bubble`.
   Make sure you
   test a few different dataypes and vary the starting (`lo`) and ending (`hi`) indices.
   Once your group is confident that the code compiles and runs correctly,
   check `checkstyle`, then stage and commit `BubbleSort.java` to your local repository
   with message `"checkpoint-2"`, then **push the changes** up to GitHub. 

1. **GROUP MEMBER 2:** Pull the changes to your local copy of the repository, if needed.
   
1. **EVERYONE:** View the condensed, graphical version of your Git log using `git adog`.

<hr/>

![CP](https://img.shields.io/badge/Just%20Finished%20Checkpoint-2-success?style=for-the-badge)

<hr/>

### Checkpoint 3 Steps

**Bubble Sort Algo**: This method also takes an array, two valid index positions `lo` and `hi` (both inclusive) 
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
      bubbleSort(array, 0, 4, Integer::compareTo);
      System.out.println(Arrays.toString(array)); // [ 1, 2, 3, 4, 5 ]
      ```
1. **GROUP MEMBER 2:** Implement the `bubbleSort` 
   method in `BubbleSort.java`. 
   
1. **GROUP MEMBER 2:** Write some code in the `main` method to test the implementation of `bubbleSort`. You can
   most likely use your `bubble` tests - just change them to do a full `bubbleSort`. Make sure 
   you test a few different dataypes and vary the starting (`lo`) and ending (`hi`) indices.
   Once your group is confident that the code compiles and runs correctly,
   check `checkstyle`, then stage and commit `BubbleSort.java` to your local repository
   with message `"checkpoint-3"`, then **push the changes** up to GitHub. 

1. **GROUP MEMBER 1:** Pull the changes to your local copy of the repository, if needed.
   
1. **EVERYONE:** View the condensed, graphical version of your Git log using `git adog`.

<hr/>

![CP](https://img.shields.io/badge/Just%20Finished%20Checkpoint-3-success?style=for-the-badge)

<hr/>

### Checkpoint 4 Steps

1. **GROUP MEMBER 1:** Create a plain text file called `NOTES.md` using the following as a template:

   ````
   # Notes
   
   ## Bubble Sort Algo
   
   ```java
   void bubble(array, lo, hi, c) {
       // REMEMBER, n = hi - lo + 1
       // REPLACE: WITH INSIDE OF YOUR bubble METHOD
   } // bubble
   ```
   
   ```java
   void bubbleSort(array, lo, hi, c)
       // REMEMBER, n = hi - lo + 1
       // REPLACE: WITH INSIDE OF YOUR bubbleSort METHOD
   } // bubble
   ```
   ````
   
   In this file, replace the comments labeled `REPLACE` with the bodies of your `bubble` and `bubbleSort`
   methods.
   
   * In Emacs? Use `C-x 3` to open a second buffer, `C-x o` to move to the other buffer, then
     `C-x f` to find/open the relevant `.java` file. Select and copy text as usual, then use
     `C-x o` to move back to the first buffer to paste.
   
   In this file, derive timing functions for two different algorithm analyses of the **Bubble Sort Algo**. 
   Here, let the problem size be defined as `n = hi - lo + 1`. Use the following as a guide
   
   1. What is `T(n)` for a direct call to `bubble` if the set of key processing steps includes
      only comparison operations (i.e., calls to `c.compare`)? Include the diagram
      for your derivation as comments in your code, similar to what is show in the required readings. 
      
   1. What is `T(n)` for a call to `bubbleSort` if the set of key processing steps includes
      only comparison operations (i.e., calls to `c.compare`)? Include the diagram
      for your derivation as comments in your code snippet, similar to what is show in the 
      required readings. As `bubbleSort` calls `bubble`, this will involve mathematical 
      function composition. 

1. **GROUP MEMBER 1:** Once your group is confident that the code compiles and runs correctly,
   stage and commit `NOTES.md` to your local repository
   with message `"checkpoint-4"`, then **push the changes** up to GitHub.
   
1. **GROUP MEMBER 2:** Pull the changes to your local copy of the repository, if needed.
   
1. **EVERYONE:** Look at the `NOTES.md` file on GitHub.

<hr/>

![CP](https://img.shields.io/badge/Just%20Finished%20Checkpoint-4-success?style=for-the-badge)

<hr/>

### Submission Steps

**Each student needs to individually submit their own work.**

1. Create a plain text file called `SUBMISSION.md` directly inside this exercise
   directory with the following information:

   1. Your name and UGA ID number;
   1. Collaborator names, if any; and
   1. The weekly code (listed with the exercise on eLC).
   
   Here is an example:
   
   ```
   1. Sally Smith (811-000-999)
   2. Collaborators: Joe Allen, Stacie Mack
   3. Weekly Code: replace-with-actual-code
   ```

1. Add and commit `SUBMISSION.md`. Also, do a final check to ensure your code 
   passes the `checkstyle` audit, then stage and commit all changes, if needed.

1. Change into the parent directory and use the `submit` command to submit this exercise to `cs1302a`:
   
   ```
   $ submit cs1302-ce25 cs1302a
   ```
     
<hr/>

![CP](https://img.shields.io/badge/Just%20Finished-Submission-success?style=for-the-badge)

<hr/>

[![License: CC BY-NC-ND 4.0](https://img.shields.io/badge/License-CC%20BY--NC--ND%204.0-lightgrey.svg)](http://creativecommons.org/licenses/by-nc-nd/4.0/)

<small>
Copyright &copy; Michael E. Cotterell, Brad Barnes, and the University of Georgia.
This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/4.0/">Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International License</a> to students and the public.
The content and opinions expressed on this Web page do not necessarily reflect the views of nor are they endorsed by the University of Georgia or the University System of Georgia.
</small>
