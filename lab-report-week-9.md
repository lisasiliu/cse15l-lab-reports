# Week 9 Lab Report

**Assignment:** Instructions [here](https://ucsd-cse15l-f22.github.io/week/week8/#lab-report-5).

---

### grade.sh
```
# INCOMPLETE

set -e

rm -rf student-submission
git clone $1 student-submission

# Check that the student code has the correct file submitted. 
#If they didn’t, detect and give helpful feedback about it.
# Useful tools here are if and -e/-f. You can use the exit command to quit a bash script early.

echo ""

cd student-submission

if test -e "ListExamples.java";
then
    echo "ListExamples.java has been found"
else
    echo "ListExamples.java has not been found"
    exit 1;
fi

# Somehow get the student code and your test .java file into the same directory
# Useful tools here might be cp and maybe mkdir

cd .. 
cp TestListExamples.java student-submission
cd student-submission

echo "Test file loaded"

# Compile your tests and the student’s code from the appropriate directory 
# with the appropriate classpath commands. 
# If the compilation fails, detect and give helpful feedback about it.
# --
# Aside from the necessary javac, useful tools here are output redirection 
# and error codes ($?) along with if

CP="../lib/junit-4.13.2.jar;lib/hamcrest-core-1.3.jar" 

javac -cp $CP *.java

echo "Files compiled"

# This might be a time where you need to turn off set -e. Why?

set +x

# Run the tests and report the grade based on the JUnit output.
# Again output redirection will be useful, and also tools like grep could be helpful here

JCORE="org.junit.runner.JUnitCore"

java -cp $CP $JCORE TestListExamples
```

### 3 Screenshots



