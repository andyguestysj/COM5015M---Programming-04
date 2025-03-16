# File I/O & Serialisation Extra

## Setting Up A Project

### Setting Up A Project

1. Get a GitHub account
2. Setting Up Visual Studio Code
   1. Connect To GitHub
   2. Set up git details
3. Clone The Starter Project
   1. Cloning A Project
   2. Disconnect From Source   
   3. Rename Template
   4. Publish To Your GitHub
4. Working With Your Project
   1. Commit changes locally
   2. Push to remote repository
   3. Cloning to a new location
   4. Pulling changes

### 1. Get A Git Account

Go to www.github.com and register an account. I recommend creating one for your uni work and only your uni work. You can have multiple accounts. Use a sensible username, you will be submitting coursework using it!

### 2. Setting Up Visual Studio Code

1. Connect to GitHub
   1. Click on the symbol of a person in a circle at the bottom left of the VSC window.
   2. Click "Settings Sync", choose "Sign in with GitHub"
   3. Follow instructions
   4. Your settings can now be sync'd between computers.
2. Set up git details
   1. In the terminal window enter the following commands
         ```
         git config --global user.name "Your Name"
         git config --global user.email "you.email@yorksj.ac.uk"
         ```
   2. You will need to do this on each new mchine you use.

### 3. Clone The Starter Project

1. Cloning A Project
   1. Copy the URL for the project you want to clone
   
      For Programming 04 David's default starter project is
         ```
         https://github.com/davidgundry/java-maven-template.git
         ```
      Repositories may be given to you as a link. You can get the clone link from the repository page. Often there is a green "Code", "Clone" or "Download" button. Press it, select the HTTPS option and copy the link.
   2. Go to VSC. Ensure that the current folder is closed. (Menu - File - Close Folder)
   3. Click the Source Control button in the left hand bar
   4. Click "Clone Repository"
   5. Paste the copied link in to the text box and press return
   6. Browse to the folder you wish to put the downloaded code folder in to.
         ```
         **Note** You are picking the folder to put a folder in to. If you create a folder called "My Project" and select it then you will end up with a folder inside My Project and everything you have downloaded will be in it. If you want to create a project inside a folder called "Code", select the code folder.
         ```
   7. Wait for the repository to download and open it.
2. Disconnect from the source
   
   At this point you have the code and a local copy of the repository on your computer. That repository is still linked to David's source repository. If you try to save changes to the repository (by `Committing` them) and `Push` those changes to the remote repository you will not be able to because you do not have permission to do so.

   To save your changes remotely you need to disconnect from David's repository so you can connect to your own. You can do this by following the steps below.

   1. Ensure you have the repository folder open in VSC
   2. Click the Source Control button in the LHS button bar.
   3. Look for the heading **Repositories**. There should be only one entry under this heading.
   4. At the end of the line for the repository is an icon of three dots in a row. Click this button
   5. From the pop up menu select **Remote** and then **Remove Remote**
   6. At the top of the screen you should see a drop down menu with one item. Select the item.
   
   Your local repository is now disconnected from David's repository. Next step is to create a new repository of your own.

3. Rename Template
   
   1. Close VSC
   2. Browse to the folder containing your project
   3. Change the name of the folder
   4. Re-open VSC
   5. Open folder using menu "File - Open Folder..". Select the project folder and press OK.

   That's it. Its fiddly but if you don't you'll end up with every foler with the same name with a bunch of numbers added on.

4. Publish your Github
   
   1. Ensure project folder is open
   2. Click on the `Source Control` button in the LHS bar
   3. Click `Publish Branch`
   4. Select `Publish to GitHub public repository...`
   
   If you've connected successfully to Github before this then that's all you need to do. If not you will be asked to sign in to GitHub.

### 4. Working with your project

1. Commit changes locally
   
   When you make changes to your code they don't automatically update either your local or remote repository. To save the changes to the **local** repository you must `Commit` them.

   1. Make change to code.
   2. Click `Source Control` button.
   3. In sidebar click in the text box "Message (Ctrl+Enter to ...)"
   4. Enter a *useful*  commit message. It should be a brief description of the type of changes made. This is easier if you commit your changes regularly after small changes rather than at the end of a session..
   5. Press the big blue `Commit` button.
   
   This has saved the changes to the local repository but made no changes online. To save the changes online you need to `Push` them there.

2. Push to remote repository

   After `Committing` your changes locally.

   1. Click the big blue button that that says something like `Sync..` or `Push..`

   That's it!

3. Cloning to a new location
   
   Imagine you've started a new project in class, made changes, commited and pushed those changes to a repository and want to work on the project at home or next week you are at a different computer and your project is missing, what do you do?

   Simply get the URL from your GitHub repository and then clone the code to the new machine. 

   Since it is cloned from your repository you don't need to disconnect from the remote.

4. Pulling changes

   Last quick note. Lets say you worked on the code in the lab, pushed to the remote repository, went home, cloned that repository, made changes and pushed those changes to the repository. Next week in the lab you sit down at your computer and realise the code on that machine doesn't have any of the changes that you made at home. What do you do?

   Easy, simply `Pull` the changes to your machine.

   1. Open the project
   2. Click the `Source Control` button
   3. Click the three dots on the line for your repository
   4. Select `Pull, Push - Pull` from the pop up menu.
   
   Your code should now be updated to match the repository.

### Summary

* `Clone` a source repository
* Disconnect from the source
* `Publish` to your own remote repository
* `Commit` changes to your local repository
* `Push` changes from your local repository to your remote repository
* `Pull` changes from your remote repository to your local repository and your project.
  



