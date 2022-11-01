# Week 5 Lab Report

**Assignment:** Instructions [here](https://ucsd-cse15l-f22.github.io/week/week5/).

---

### **Command: Find**

**Command 1.** `find -name`

Find files by their file name instead of by their contents (case sensitive)

1. Finding all files in the folder ./technical that contain "[something]26.txt" in its name, somewhere. Useful for finding files of the type (like .txt) you want.
<img width="468" alt="image" src="https://user-images.githubusercontent.com/44093048/199104969-bf4e0751-dc27-4648-8adb-7f43b39d8561.png">

Command:
```
 find ./technical -name "*26.txt"
```

Output:
```
./technical/biomed/1471-2105-3-26.txt
./technical/biomed/1471-2105-4-26.txt
./technical/biomed/1471-2164-3-26.txt
./technical/biomed/1471-2164-4-26.txt
./technical/biomed/1471-2180-1-26.txt
./technical/biomed/1471-2180-2-26.txt
./technical/biomed/1471-2334-2-26.txt
./technical/biomed/gb-2003-4-4-r26.txt
./technical/government/Gen_Account_Office/og96026.txt
./technical/government/Gen_Account_Office/og98026.txt
./technical/plos/pmed.0010026.txt
./technical/plos/pmed.0020226.txt
```


2. Finds all files in the folder ./technical that contain "og98" in its name (letters before and after don't matter). Useful for finding files that have the keywords (like og98) you want.
<img width="494" alt="image" src="https://user-images.githubusercontent.com/44093048/199105824-87fcc3dd-ce86-444d-9174-469be5291324.png">

Command:
```
 find ./technical -name "*og98*"
```

Output:
```
./technical/government/Gen_Account_Office/og98018.txt
./technical/government/Gen_Account_Office/og98019.txt
./technical/government/Gen_Account_Office/og98022.txt
./technical/government/Gen_Account_Office/og98024.txt
./technical/government/Gen_Account_Office/og98026.txt
./technical/government/Gen_Account_Office/og98029.txt
./technical/government/Gen_Account_Office/og98030.txt
./technical/government/Gen_Account_Office/og98032.txt
./technical/government/Gen_Account_Office/og98040.txt
./technical/government/Gen_Account_Office/og98041.txt
./technical/government/Gen_Account_Office/og98044.txt
./technical/government/Gen_Account_Office/og98045.txt
./technical/government/Gen_Account_Office/og98046.txt
```


3. Different result (no results) compared to before because `-name` is case sensitive, so it doesn't match anything. 
Finds all files in the folder ./technical that contain "OG98" in its name (letters before and after don't matter).
Useful for realizing that some commands are case sensitive.
<img width="467" alt="image" src="https://user-images.githubusercontent.com/44093048/199105991-700c4b7e-0339-4241-9984-7fa1fabc6b4b.png">

Command:
```
 find ./technical -name "*OG98*"
```

Output:
```

```

**Command 2.** `find -iname`

Find files by their file name (case insensitive)

1. Finding all files in the folder ./technical that contain "[something]26.txt" in its name, somewhere. Useful for finding files of the type (like .txt) you want.
<img width="485" alt="image" src="https://user-images.githubusercontent.com/44093048/199106936-609f8e6e-6348-4894-95de-4aee0fbe4e78.png">

Command:
```
 find ./technical -iname "*26.txt"
```

Output:
```
./technical/biomed/1471-2105-3-26.txt
./technical/biomed/1471-2105-4-26.txt
./technical/biomed/1471-2164-3-26.txt
./technical/biomed/1471-2164-4-26.txt
./technical/biomed/1471-2180-1-26.txt
./technical/biomed/1471-2180-2-26.txt
./technical/biomed/1471-2334-2-26.txt
./technical/biomed/gb-2003-4-4-r26.txt
./technical/government/Gen_Account_Office/og96026.txt
./technical/government/Gen_Account_Office/og98026.txt
./technical/plos/pmed.0010026.txt
./technical/plos/pmed.0020226.txt
```


2. Finds all files in the folder ./technical that contain "og98" in its name (letters before and after don't matter). Useful for finding files that have the keywords (like og98) you want.
<img width="484" alt="image" src="https://user-images.githubusercontent.com/44093048/199107037-3d36ccc8-7535-430e-92f4-93b196879ed4.png">

Command:
```
 find ./technical -iname "*og98*"
```

Output:
```
./technical/government/Gen_Account_Office/og98018.txt
./technical/government/Gen_Account_Office/og98019.txt
./technical/government/Gen_Account_Office/og98022.txt
./technical/government/Gen_Account_Office/og98024.txt
./technical/government/Gen_Account_Office/og98026.txt
./technical/government/Gen_Account_Office/og98029.txt
./technical/government/Gen_Account_Office/og98030.txt
./technical/government/Gen_Account_Office/og98032.txt
./technical/government/Gen_Account_Office/og98040.txt
./technical/government/Gen_Account_Office/og98041.txt
./technical/government/Gen_Account_Office/og98044.txt
./technical/government/Gen_Account_Office/og98045.txt
./technical/government/Gen_Account_Office/og98046.txt
```


3. Same result compared to before because `-iname` is NOT case sensitive. 
Finds all files in the folder ./technical that contain "OG98" in its name (letters before and after don't matter).
Useful because now you don't have to remember the specific case of keywords when using the command to find matching files.
<img width="488" alt="image" src="https://user-images.githubusercontent.com/44093048/199107106-afc038be-89d5-4284-b241-a7c7cb586230.png">

Command:
```
 find ./technical -iname "*OG98*"
```

Output:
```
./technical/government/Gen_Account_Office/og98018.txt
./technical/government/Gen_Account_Office/og98019.txt
./technical/government/Gen_Account_Office/og98022.txt
./technical/government/Gen_Account_Office/og98024.txt
./technical/government/Gen_Account_Office/og98026.txt
./technical/government/Gen_Account_Office/og98029.txt
./technical/government/Gen_Account_Office/og98030.txt
./technical/government/Gen_Account_Office/og98032.txt
./technical/government/Gen_Account_Office/og98040.txt
./technical/government/Gen_Account_Office/og98041.txt
./technical/government/Gen_Account_Office/og98044.txt
./technical/government/Gen_Account_Office/og98045.txt
./technical/government/Gen_Account_Office/og98046.txt
```

**Command 3.** `find -empty`

Finds empty files

1. Finds any files in ./technical that are empty (there are none here)
<img width="416" alt="image" src="https://user-images.githubusercontent.com/44093048/199107330-858f5944-07a5-4ded-90aa-36dbe5e934d9.png">
Command:

```
 find ./technical -empty
```

Output:
```

```

2. Created a new file in ./technical that is empty using vim (emptyfile.txt). Now there are empty (currently without a use) files that can be deleted/used.
<img width="656" alt="image" src="https://user-images.githubusercontent.com/44093048/199107686-65ec2d07-11ca-42ae-9440-ed40c36775c9.png">

Command:
```
 find ./technical -empty
```

Output:
```
./technical/emptyfile.txt
```

3. Created another empty file in ./technical using vim (emptyfile2.txt). Another empty file to check and reuse.
<img width="418" alt="image" src="https://user-images.githubusercontent.com/44093048/199107922-02984f91-ca82-4d73-a387-372e7527f682.png">

Command:
```
 find -empty
```

Output:
```
./emptyfile.txt
./emptyfile2.txt
```



