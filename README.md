# cs1302-ce27 Preparing for Paired Programming

![Approved for: Fall 2019](https://img.shields.io/badge/Approved%20for-Fall%202019-brightgreen)
<!--![Approved for: Spring 2020](https://img.shields.io/badge/Approved%20for-Spring%202020-blue)
![Instruction: Online](https://img.shields.io/badge/Instruction-Online-important)-->

In this class exercise, students will prepare for the next exercise by ensuring
their GitHub accounts and private repositories are setup correctly. Code
and notes will be shared between group members via a private Git repository. 


## Course-Specific Learning Outcomes
* **LO3.d:** Apply pair-programming principles in a software-based project.
* **LO5.a:** Utilize a version control tool such as Git or Subversion to store and update source code in a multi-programmer software solution.

## References and Prerequisites

* [Setting up your own GitHub Account](https://github.com/cs1302uga/cs1302-tutorials/blob/master/github-setup.md)

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

## Exercise Steps

1. To get the most out of this exercise, we encourage you to
   **form a group of exactly two people for this exercise.**
   
   * When done in a group, some steps in this exercise need be done by each group member individually.
   
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
   
**CHECKPOINT**

<hr/>

1. **Pick an ordering for the group members** (e.g., Group Member 1, Group Member 2, etc.).
   If a step is being performed by one group member, then everyone is expected
   to watch, pay attention, and take notes.

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

   1. Before proceeding, ensure that all tracked files are committed. 

   1. Visit the repository website on GitHub and copy the "SSH" URL (i.e., the `git@github...` URL)
      under "Quick setup", then follow these instructions on Nike to link your local repository 
      to the one on GitHub:
      
      ```
      $ git remote add origin git@github.com:group_member_one/cs1302-ce27-ce28.git
      $ git push -u origin master
      ```
      
      If successful, everyone should now be able to see the exercise files on the
      repository website on GitHub!

1. **OTHER GROUP MEMBERS:** Visit the repository website on GitHub and copy the "SSH"
   URL from the green "Clone or download" button, then these instructions on Nike to 
   clone the GitHub-hosted Git repostory on your Nike account:
   
   ```
   $ git clone git@github.com:group_member_one/cs1302-ce27-ce28.git
   ```
   
   Change into the directory and confirm that everything is there! You can verify that
   the origin of the `clone` operation is the repository instance on GitHub by
   using the following command:
   
   ```
   $ git remote -v
   ```
   
1. **NEXT GROUP MEMBER:** On Nike, write out the basic skeleton code for a driver class
   in `BubbleSort.java` (you don't need to implement it now; we'll write the algorithm 
   in there later), ensuring that the  package statement is correct and the file compiles 
   and runs using Maven. Then, stage and commit the change to your local repository.
   
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

[![License: CC BY-NC-ND 4.0](https://img.shields.io/badge/License-CC%20BY--NC--ND%204.0-lightgrey.svg)](http://creativecommons.org/licenses/by-nc-nd/4.0/)

<small>
Copyright &copy; Michael E. Cotterell, Brad Barnes, and the University of Georgia.
This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/4.0/">Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International License</a> to students and the public.
The content and opinions expressed on this Web page do not necessarily reflect the views of nor are they endorsed by the University of Georgia or the University System of Georgia.
</small>
