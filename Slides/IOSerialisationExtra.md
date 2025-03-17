# File I/O & Serialisation Extra

### Topics
1. Setting Up A Project
2. Creating A Simple Logger
3. Saving A Single Object
4. Saving An Array List Of Objects

Source Repository https://github.com/andyguestysj/serialisation.git


## Setting Up A Project

### Setting Up A Project

Video - https://hmlupload.yorksj.ac.uk//Home/PlayTransfer/50998

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
  

## Creating A Simple Logger

   In this section we are going to create a simple Logger class. 
   
   This will be a very simple logger that is created when an application starts, provides a simple function that takes a string as an argument and writes that string to a file. The class will need to ensure any errors/exceptions are dealt with and that the file is closed properly before the code exits.

   Video - https://hmlupload.yorksj.ac.uk//Home/PlayTransfer/51001


### Approach - Top Down

   I'm going to demonstrate this using a top down approach. In this apporach you start with the big concepts and put off worrying about the specifics/details of how things will be done until you need to worry about them.

### Step One - A Logger Class

   We need a logger class if we are going to make a logger class! We aren't going to worry about how it works, just about making it.

   1. Add a new class - Logger
   
      Right click on the project in the Explorer side bar and select "New Java File - Class..." from the pop up menu. Enter "Logger" in the text box and press enter
   
   2. Create a Logger object
   
      We've created a Logger class, we need to create a Logger object to use it. 
      
      Switch to the `App.java` file and at the start of the main function create a logger object.

      ```java
      public static void main(String[] args) {        
        Logger logger = new Logger();
      ```
   
   3. Create a log file
   
      We've got a logger object. We know its job is to write messages to a log file so we obviously need a log file. Its only a simple logger, its only going to write to a single file. So we need a file name, and we'll need to know where that file is so we need a folder.

      Lets create a `constructor` for **Logger** that takes two strings (a folder and a filename) and creates that file in that folder, ready for messages to be written to.

      We want to create a file in a folder so we have a few things to do:

      1. Check if the folder exists and if it doesn't then create it
      2. Make the file and prepare it for writing
      3. Ensure the program exits if we can't create the file so we don't try writing to a bad file handle.
   
         ```java
         public class Logger {
  
            OutputStream output;
         
            Logger(String folder, String file){
               // Check to see if the output folder exists and if does not then make it
               File folderHandle = new File(folder);
               if (!folderHandle.exists())
               {
                  folderHandle.mkdirs();
               }

               // create/open the file for logging
               try {
                  output = new FileOutputStream(folder+"\\"+file,true); // true to append, false/missing to create new blank file
               }
               catch (IOException e)
               {
                  // exit if we fail
                  throw new RuntimeException(e);
               }
            }
         }
         ```

         We've created a class variable to hold the handle to the file `output`. We know we need that handle to close the file and to write to it and we aren't doing that in the constructor so we need to store that handle for later use.

         This isn't the best code. It doesn't check to see if the folder can be made because we are going to use a sub folder of the project we will be able to make.
         
         It also exits the code if the file can't be made. A better logger would instead note that it couldn't create the log file so that attempts to write to the log file resulted in output to the screen but let the app keep running. Its unlikely that not being able to write to a log should prevent an app doing whatever else it needs to do.

         But this a simple logger so it will do.

         We can update our `App.java` with the constructor arguments.

            ```java
            public static void main(String[] args) {        
               Logger logger = new Logger("iofiles","log.txt");
            }
            ```
   4. Close the logger file
   
      Exiting an app with handled still connected to objects is bad practice. Especially when those handles are holding files open. If we don't ensure the file is closed before we exit the app the file may be locked open and/or some of the log messages may be lost.

      Here we create a `tidyUp` method in `Logger` that will be called before the app ends to close the folder.

      ```java
      public void tidyUp(){
         // close the file safely
         try {
            output.close();
         }
         catch (IOException e)
         {
            throw new RuntimeException(e);
         }
      }
      ```

      Back in `App.java` we ensure that `tidyUp()` is called just before it exits.

      ```java
      public static void main(String[] args) {        
         Logger logger = new Logger("iofiles","log.txt");





         logger.tidyUp();
      }
      ```

   5. Writing a message to the log file
   
   So our top down approach has meant our app opens and safely closes a log file. Great, but how do we write to it?

   We need a public method `log` which takes a string argument. This way we can let anyone who has access to the logger write to the file.

   ```java
   public void log(String logString){
      // write safely to file or crash gracefully(ish)
      try {
         output.write(logString.getBytes());
         output.write(System.lineSeparator().getBytes());
      }
      catch (IOException e)
      {
         throw new RuntimeException(e);      
      }
   }
   ```

   Outputting to the file is really easy. We already have the file handle so all we have to do is use the `write` command and the `getBytes()` method to send the string to the file.

   The line 
   ```java
   output.write(System.lineSeparator().getBytes());
   ```
   simply adds a new line at the end of the message so we don't end up with a long mess of text.

   We can make it a bit more useful by adding a timestamp to the start of the message as shown below.

   ```java
     public void log(String logString){


    // write safely to file or crash gracefully(ish)
    try {
      LocalTime now = LocalTime.now();
      DateTimeFormatter formatter = DateTimeFormatter.ofPattern("hh:mm:ss");
      String timeStamp = "["+now.format(formatter)+"] ";
      output.write(timeStamp.getBytes());
      output.write(logString.getBytes());
      output.write(System.lineSeparator().getBytes());
    }
    catch (IOException e)
    {
      throw new RuntimeException(e);      
    }
  }
  ```

  That's our logger done. We've created the file when the `Logger` object is created and we've created `tidyUp()` so that the file is close before the app exits.

  Anywhere in our code we want to write a log message we simple call

  ```java
  logger.log("Desired log message");
  ```

## A Simple App

   I'm going to create a simple app that stores data on students. It is a very simple app. All it does is store data.

### A Student Class

   We'll start with a basic `Student` class to hold the details of a single student.

   ```java
   package com.example;

   import java.io.Serializable;

   public class Student {

      String name;
      String className;
      String rollNo;
   
      //Constructor.
      Student(String name, String className, String rollNo){
         this.name = name;
         this.className = className;
         this.rollNo = rollNo;       
      }

      public void displayStudent(){
         System.out.println(this.name + ", " + this.className + ", " + this.rollNo);
      }

      public String getName() { return name;}

   }
   ```

   Like I said, a very simple class. It stores name, className and rollNo for a student. It has a simple display method and a method that returns a student's name.

   We'll make one simple change. We want to log whenever a new student is added to the system. So now the constructor needs access to the logger.

   ```java
      //Constructor.
      Student(String name, String className, String rollNo, Logger logger){
         this.name = name;
         this.className = className;
         this.rollNo = rollNo;

         logger.log("Student created [" + this.name + ", " + this.className + ", " + this.rollNo + "]");
      }
   ```

   Now every time a student is created the students details should be written to the log.

   We can test this.

   ```java
   public static void main(String[] args) {        
      Logger logger = new Logger("iofiles","log.txt");

      Student aStudent = new Student("John Smith","Art","11232",logger);

      logger.tidyUp();
   }
   ```

## Saving A Single Object

Vide0 - https://hmlupload.yorksj.ac.uk//Home/PlayTransfer/50999

   1. Make Student Serializable

   We're storing data in an object, how do we save that data? We don't want to have to store each bit of data one by one so we need to make the class `Serializable`. Fortunately thats nice and easy.

   ```java
   public class Student implements Serializable{
   ```

   We just have to make the `Student` class inherit from `Serializable`.

   2. A File I/O Class
   
   I'm going to make a class which handles saving object data and I'm going to call it `FileIO`.
   
   ```java
      public class FileIO {

      String folder;

      FileIO(String folder) {

         this.folder = folder;
         File folderHandle = new File(folder);
         if (!folderHandle.exists()) {
            folderHandle.mkdirs();
         }

      }
   }
   ```

   Top down approach remember? We need a class that will store data in files (and eventually load data from files), it needs to know where to store the files and we need to make sure that location exits.

   We add the line

   ```java
   FileIO fileHandler = new FileIO("iofiles");
   ```

   as the first line in `main`.

   3. Saving A Student Object

   We create a `saveStudent` method. It takes as arguments a student object, a string with the name of the file to save the student data to, and the logger handle so we can log what we've done.

   ```java
   public void saveStudent(Student s, String file, Logger logger) {
      try (
         // Creating FileOutputStream object.
         FileOutputStream fos = new FileOutputStream(folder + "\\" + file);
         // Creating ObjectOutputStream object.
         ObjectOutputStream oos = new ObjectOutputStream(fos);) {
         // write object.
         oos.writeObject(s);
         logger.log("Student [" + s.getName() + "] saved to file [" + folder + "\\" + file +"]");

      } catch (IOException e) {
         throw new RuntimeException(e);
      }
   }
   ```   

### Loading A Single Object
   
   We create a `loadStudent` method. It takes as arguments a string with the name of the file to save the student data to, and the logger handle so we can log what we've done and returns a student object.

   ```java
   public Student loadStudent(String file, Logger logger) {
      try (
         // Creating FileOutputStream object.
         FileInputStream fis = new FileInputStream(folder + "\\" + file);
         // Creating ObjectOutputStream object.
         ObjectInputStream ois = new ObjectInputStream(fis);) {
         // load object

         // write object.
         Student s = (Student) ois.readObject();
         logger.log("Student [" + s.getName() + "] loaded from file [" + folder + "\\" + file +"]");
         return s;
      } catch (IOException e) {
         throw new RuntimeException(e);
      } catch (ClassNotFoundException e) {
         throw new RuntimeException(e);
      }
      
   }
   ```

   We have to cast the object that has beed read in back to `Student`. If the data isn't actually a student this could cause problems. But wwe are cocky programmers and we know that file will only contain a student object so we risk it..

   We can test this by adding the following lines to main after we create the student object.

   ```java
   fileHandler.saveStudent(aStudents, "student_save.ser",logger);
   fileHandler.loadStudent("student_save.ser",logger).displayStudent();
   ```

### A Student List Class

   Storing information on a single student isn't much use and we'd rather have some sort of collection of students rather than a load of distinct student objects with different names. 

   So we will use an array list.
   
   This should be pretty simple. 

   We are going to store the handle for the logger in the StudentList class. This makes the rest of the cose tidier but means we can only use the one log file here. Both approaches are fine, it depends on your requirements.

   We will see why `setStudentList` is required when we look at loading an array of student data.

   ```java
   public class StudentList {

      Logger logger;

      private ArrayList<Student> students = new ArrayList<Student>();

      StudentList(Logger logger){		
         this.logger = logger;
         logger.log("Student list created");
      }

      public void addStudent(String name, String className, String rollNo){
         students.add(new Student(name, className, rollNo, logger));    
         logger.log("Student added to list [" + name + ", " + className + ", " + rollNo + "]");
      }

      public void displayList(){
         System.out.println("List contains:");
         for (Student s:students){
            System.out.print("\t");
            s.displayStudent();
         }      
      }

      public Student getStudent(){
         return students.get(0);
      }

     public  ArrayList<Student> getArray() { return students;}

      public void setStudentList(ArrayList<Student> arrayStudents, Logger logger){
         students = (ArrayList)arrayStudents.clone();
         logger.log("Student list cloned");
      }

      public void populateStudentList(Logger logger){
         String theStudents[][] = {
            {"John Smith","Art","11932"},
            {"Sally Brown","Maths","13154"},
            {"Tom Hanks","History","98872"},
            {"Chloe Burns","Art","72893"},
            {"Halle Berry","Physics","43451"}
         };

         for (int i = 0; i< theStudents.length; i++){
            addStudent(theStudents[i][0],theStudents[i][1],theStudents[i][2]);
         }

            logger.log("Student list populated");
      }
   }
   ```
## Saving An Array List Of Objects

   Turns out that saving an array of objects is pretty much the same as saving a single object.

   video - https://hmlupload.yorksj.ac.uk//Home/PlayTransfer/51000

   ```java
   public void saveStudentList(StudentList sl, String file, Logger logger) {
      try (
         // Creating FileOutputStream object.
         FileOutputStream fos = new FileOutputStream(folder + "\\" + file);
         // Creating ObjectOutputStream object.
         ObjectOutputStream oos = new ObjectOutputStream(fos);) {
         // write object.
         oos.writeObject(sl.getArray());
         logger.log("Student list saved to file [" + folder + "\\" + file +"]");

      } catch (IOException e) {
         throw new RuntimeException(e);
      }
   }
   ```

   Only difference is we pass in an array list of objects rather than a single object.

   **Note** note that we aren't saving a single `StudentList` object, we are saving the array list of `Student` objects `students` from within `studentList`.

### Loading An Array List Of Objects

   This is a little trickier.

   ```java
   public  ArrayList<Student> loadStudentList(String file, Logger logger) {
      try (
         // Creating FileOutputStream object.
         FileInputStream fis = new FileInputStream(folder + "\\" + file);
         // Creating ObjectOutputStream object.
         ObjectInputStream ois = new ObjectInputStream(fis);) {
         // load object

         // write object.
         ArrayList<Student> sl = ( ArrayList<Student>) ois.readObject();
         logger.log("Student list loaded from file [" + folder + "\\" + file +"]");
         return sl;
      } catch (IOException e) {
         throw new RuntimeException(e);
      } catch (ClassNotFoundException e) {
         throw new RuntimeException(e);
      }
      
   }
   ```

   We have to cast the loaded object data as an array list of Students (with all the risks mentioned in loading a single object).

   What we end up with is an array list of Students and we want it to be stored in a `StudentList` object so we have to create that object and use the loaded list to populate it.

   Our main looks something like this.

   ```java
      public static void main(String[] args) {

         FileIO fileHandler = new FileIO("iofiles");
         Logger logger = new Logger("iofiles","log.txt");
         StudentList allStudents = new StudentList(logger);

         allStudents.addStudent("James", "Art", "15404");        
         allStudents.populateStudentList(logger);
         allStudents.displayList();

         fileHandler.saveStudent(allStudents.getStudent(), "student_save.ser",logger);
         fileHandler.loadStudent("student_save.ser",logger).displayStudent();

         fileHandler.saveStudentList(allStudents, "student_save.ser", logger);

         StudentList newList = new StudentList(logger);
         newList.setStudentList(fileHandler.loadStudentList("student_save.ser", logger), logger);

         newList.displayList();

         logger.tidyUp();


      }
   ```

## Summary

### Topics
1. Setting Up A Project
2. Creating A Simple Logger
3. Saving A Single Object
4. Saving An Array List Of Objects

Source Repository https://github.com/andyguestysj/serialisation.git
