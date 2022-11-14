# Lab Report 4

## Part 1 

I chose the task of Changing the name of the *start* parameter and its uses to *base*

```
/start<Enter> ce base<Esc> n . n . :wq<Enter>
```

![Image](https://raw.githubusercontent.com/NicholasLam1/cse15l-lab-reports/main/lab4pic1.png)

This shows the screen when typing /start which finds the instances of start and moves the cursor there.


![Image](https://raw.githubusercontent.com/NicholasLam1/cse15l-lab-reports/main/lab4pic2.png)

This shows the screen after typing ce which put vim into input mode and deleted the word start.


![Image](https://raw.githubusercontent.com/NicholasLam1/cse15l-lab-reports/main/lab4pic3.png)

This shows the screen after typing base.

![Image](https://raw.githubusercontent.com/NicholasLam1/cse15l-lab-reports/main/lab4pic4.png)

This shows the screen after hitting Esc which put vim back into normal mode and after hitting n which found the next instance of start.


![Image](https://raw.githubusercontent.com/NicholasLam1/cse15l-lab-reports/main/lab4pic5.png)

This shows the screen after hitting . which repeated the last command and then hitting n and . again which replaced the last instance of start with base. 

![Image](https://raw.githubusercontent.com/NicholasLam1/cse15l-lab-reports/main/lab4pic6.png)

This shows the screen after making all the changes and typing :wq which would save and close. 



## Part 2

It took around 49 seconds for the first method and around 18 seconds for the second method. The first method was slower due to having to wait for the file to transfer over and having to login. 

I would prefer making the edit while already logged into a ssh session since it was faster for me. It also means having to do less commands such as scp and ssh. It also avoids possible mistakes such as copying over the wrong file or having it be in the wrong directory. If the project is of a large file size, then I would go with the second method since the first method would depend on internet speed and how fast it takes to transfer the file over. If the project could somehow damage the remote server, then I may want to do the first method and test that it works as intended first before copying it over and running it remotely. 
