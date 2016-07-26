SVN Guide
=========

[Subversion (SVN)](https://en.wikipedia.org/wiki/Apache_Subversion) is a "software versioning and revision control system". It is sort of like Dropbox in that allows you to maintain a copy of your files on a remote server. This means that a hard drive crash before a deadline is never an excuse for a late assignment. SVN also keeps previous versions of your code. This is great because if you make a change and break your program you can always go back to the older, working version. Finally, SVN allows multiple programmers to collaborate on the same code, or one programmer to easily work on the same code from different computers.

## Initial Setup

1. Install SVN. You will find many distributions here: [Apache SVN Binary Packages](https://subversion.apache.org/packages.html). If you are using a Mac you may install [homebrew](http://brew.sh/) and then install SVN using ```brew install svn``` as described [here on stackoverflow](http://stackoverflow.com/questions/19921714/command-line-svn-client-for-mac). On Windows, [Tortoise SVN](https://sourceforge.net/projects/tortoisesvn/) is recommended. :warning: Make sure to get an early start so that you may seek help from the instructor, TAs, or tutoring center *before* the assignment deadline.

2. Create a CS 112 directory in your SVN repository using the following command in a terminal window: ```svn mkdir https://www.cs.usfca.edu/svn/<username>/cs112 -m "create cs 112 repo"```
Make sure to replace ```<username>``` with your username. 

3. At this point, you have only created directories on the server. No new directories will have been created on your computer. You can verify that the directory was created correctly by visiting ```https://www.cs.usfca.edu/svn/<username>```. You will be prompted for your Computer Science (not main USF!) login credentials. Once you provide them you will see a list of all repositories, which should include cs112.

4. Use the ```co``` command to check out the repository on your local computer. Use the terminal to navigate to the directory where you want to store the cs112 directory that will contain all of your work for the semester, for example something like ```/Users/srollins/classwork```. Use the command ```svn co https://www.cs.usfca.edu/svn/<username>/cs112```. You should see something like the following: ```Checked out revision 1.```. If you now type ```ls``` to list all files in the directory, you should see that the ```co``` command create a new directory ```cs112```.

## Assignments

For each assignment you will create a subdirectory in your ```cs112``` directory. Lab 1 will be submitted in a directory ```cs112/lab1```, project 1 will be submitted in a directory ```cs112/project1```, and so on.

1. Before you begin work on an assignment, use the terminal to ```cd``` into the ```cs112``` directory. 
2. **Create a new directory:** Use the ```mkdir``` (make directory) command to create a new directory for the assignment, for example ```mkdir lab1```.
3. **Save code in the new directory:**```cd``` into the appropriate assignment directory and create the necessary Java files for the assignment. 
4. **Add all directories and files:** For every major code change (*not just when you are ready to submit*), add all files and directories you wish to commit. *You do not need to add the ```.class``` files.*
  - If you have not yet added the directory, ```cd``` into the ```cs112``` directory and type ```svn add <assignment>/```, replacing assignment with ```lab1```, ```project2```, or the appropriate name. This will add the directory and all files in the directory and will display something like the following:  
   
  ```
  saison:cs112 srollins$ svn add lab1/  
  A         lab1  
  A         lab1/Test.java  
  ```
  - If the *directory* has already been added you may add individual files as follows: ```svn add filename```

5. **Commit your changes:** Once all files have been added you will *commit* your changes. This is the step that actually saves your files to the server. The command looks as follows: ```svn commit -m "adding working Hello.java"```. Inside of the quotation marks, include a message that describes the code changes you have made since the last commit. You will see a message as follows if your commit was successful:

  ```
  Transmitting file data .
  Committed revision 362.
  ```

6. **Verify your submission:** Use a browser to view the code and *confirm* the most up-to-date version has been committed. The URL should look as follows: ```https://www.cs.usfca.edu/svn/<username>/cs112/<assignment>/```.

7. **Updating:** Anytime you modify or extend your code make sure to (1) **add** any  new files (step 4); (2) **commit** changes (step 5); and (3) **verify** your submission (step 6).
  
