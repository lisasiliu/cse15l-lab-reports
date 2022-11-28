# Week 9 Lab Report

**Assignment:** Instructions [here](https://ucsd-cse15l-f22.github.io/week/week8/#lab-report-5).

---

### grade.sh
```
rm -rf student-submission
git clone $1 student-submission

echo ""

cd student-submission

if test -e "ListExamples.java";
then
    echo "ListExamples.java has been found"
else
    echo "ListExamples.java has not been found"
    echo "Grade: 1/5"
    exit 1;
fi

cd .. 
cp TestListExamples.java student-submission
cp -r lib student-submission
cd student-submission

echo "Test file loaded"

CP=".:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar" 

javac -cp $CP *.java

if [ $? -eq 0 ]
then
    echo "Files compiled successfully"
else
    echo "Files did not compile successfully"
    echo "Grade: 2/5"
    exit 1
fi

JCORE="org.junit.runner.JUnitCore"

java -cp $CP $JCORE TestListExamples
if [ $? -eq 0 ]
then
    echo "Tested successfully"
    echo "Grade: 5/5"
else
    echo "Did not test successfully"
    echo "Grade: 3/5"
fi

```

### 3 Screenshots

**1.** Correct Submission

<img width="666" alt="image" src="https://user-images.githubusercontent.com/44093048/204217339-b5bf2fb9-b230-44e9-8115-5213e64a3662.png">


**2.** Compile Error

<img width="657" alt="image" src="https://user-images.githubusercontent.com/44093048/204217462-3655fd27-9719-4bf0-9744-618ce82d0c14.png">


**3.** Wrong Filename

<img width="641" alt="image" src="https://user-images.githubusercontent.com/44093048/204217546-bea92ed4-9367-4f41-82d0-4fa4bf696d7a.png">


### Trace of Screenshot 3

```
rm -rf student-submission
```
^ stdout none - stderr none - return 0 ^ 


```
git clone $1 student-submission
```
^ stdout "Cloning into 'student-submission'..." - stderr none - return 0 ^ 


```
echo ""
```
^ stdout "" - stderr none - return 0 ^ 


```
cd student-submission
```
^ stdout none - stderr none - return 0 ^ 

```
if test -e "ListExamples.java";
```
^ feturns false, because the file submitted was not called ListExamples.java ^ 

```
then
```
^ does not run, because if statement above returned false ^ 

```
    echo "ListExamples.java has been found"
```
^ does not run, because if statement above returned false ^
    
```
else
```
^ stdout none - stderr none - return 0 ^ 

```
    echo "ListExamples.java has not been found"
```
^ stdout "ListExamples.java has not been found" - stderr none - return 0 ^ 

```
    echo "Grade: 1/5"
```
^ stdout "Grade: 1/5" - stderr none - return 0 ^ 

```
    exit 1;
```
^ stdout none - stderr none - return 1 ^ 

    
`fi` (and all lines after that) does not run because of the early exit (exit 1) in the line before.

