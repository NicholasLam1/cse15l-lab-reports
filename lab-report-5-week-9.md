# Lab Report 5

Grade.sh Code:

```
rm -rf student-submission
git clone $1 student-submission > out.txt 2> err.txt

cp TestListExamples.java lessthan5.java student-submission/
cd student-submission/

if [ -e "ListExamples.java" ]
then
    echo "Correct file"
else
    echo "Failed. Your submission should have a file named ListExamples.java"
    exit 
fi

javac -cp .:../lib/hamcrest-core-1.3.jar:../lib/junit-4.13.2.jar *.java > out2.txt 2> err2.txt

if [ $? -eq "0" ]
then
    echo "Code Compiled"    
else
    echo "Failed. Could not compile."
    exit 
fi

java -cp .:../lib/hamcrest-core-1.3.jar:../lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples > out3.txt 2> err3.txt

if [ grep EE out3.txt ]; then
    echo "Failed. Score: 0"
elif [ grep .E out3.txt ]; then
    echo "Pass. Score: 1"
elif [ grep E. out3.txt ]; then
    echo "Pass. Score: 1"
else
    echo "Pass. Score: 2"
fi
```


Screenshots of three different student submissions:

![Image](https://raw.githubusercontent.com/NicholasLam1/cse15l-lab-reports/main/lab5pic1.png)

![Image](https://raw.githubusercontent.com/NicholasLam1/cse15l-lab-reports/main/lab5pic2.png)

![Image](https://raw.githubusercontent.com/NicholasLam1/cse15l-lab-reports/main/lab5pic3.png)


A trace of grade.sh for the third example:

>git clone $1 student-submission > out.txt 2> err.txt

The standard output stored in out.txt is "" and standard error stored in err.txt is "Cloning into 'student-submission'". The return code after running echo $? is 0.

For the first if statement:
> if [ -e "ListExamples.java" ]

The condition is false since there does not exist a file named "ListExamples.java" anywhere in the directory. 
Since the condition is false, it runs echo "Failed. Your submission should have a file named ListExamples.java" and then exit.
Due to this early exit, the remaining lines after this if-statement never run.