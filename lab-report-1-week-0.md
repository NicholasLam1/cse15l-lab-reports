# Lab Report 1


**Installing VScode**

This is how the interface of Visual Studio code looks like. The first step of installing this program to the computer was going to https://code.visualstudio.com/ and downloading the Windows version. The website also has different versions specific to the type of operating system and once it is installed the color theme of the window can be customized.

**Remotely Connecting**

The cluster status message is displayed after successfully connecting remotely. The first step to connect remotely was to open a new terminal in VSCode. Then entering a command similar to: 
> ssh cs15lfa22zz@ieng6.ucsd.edu 

This did not work for me so I was instructed to use 
>ssh n2lam@ieng6.ucsd.edu 

instead. There would be a prompt asking “Are you sure you want to continue connecting?” and enter yes. Then there would be a password prompt where you will enter your password. 

**Trying Some Commands**

This shows the results of running some commands in the terminal. Specifically, I ran pwd to print which directory I am in and then used ls to print the contents of my working directory. I used cd to change the directory to Documents and then confirmed I changed directory using pwd and  the printed the contents of that directory.

**Moving Files with scp**

This shows the result after running a file that I copied from the local computer onto the remote computer. The first step was creating a WhereAmI java file that used the getProperty method to print out information about the system. Then I used the command 

>scp WhereAmI.java n2lam@ieng6.ucsd.edu:~/ 

to copy over the file. After entering the password, I used javac to compile and then java to run the actual file. 

**Setting an SSH Key**

This shows the output of running ssh-keygen in the terminal.The command first prompts which file to save the key which I hit enter to specify the default path. When asked to enter a passphrase I left it empty. The next step was to copy the public key to the .ssh directory of my user account on the server which was accomplished using 
>mkdir .ssh 

Then back on the client i used 
>scp /Users/n2lam/.ssh/id_rsa.pub n2lam@ieng6.ucsd.edu:~/.ssh/authorized_keys

 Following these steps allow the user to login to the server without entering your password.

**Optimizing Remote Running**











