---
#Part 1# 
---
Student Post 
---

Student: Hi, I'm having trouble running my Java program. I'm working on a python script that calls the program to process data but the program doesn't execute properly. I'm not sure why, but it exits with an error message.  

*DataProcessor.java:*
```
import java.io.*;

public class DataProcessor {
    public static void main(String[] args) {
        try {
            BufferedReader reader = new BufferedReader(new FileReader("data.txt"));
            String line;
            while ((line = reader.readLine()) != null) {
                System.out.println(line);
            }
            reader.close();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

*Directory Structure:*
```
project/
├── DataProcessor.java
├── data.txt
└── runner.py
```

*runner.py:*
```
import subprocess

def run_java():
    subprocess.run(["javac", "DataProcessor.java"])
    result = subprocess.run(["java", "DataProcessor"], capture_output=True, text=True)
    print(result.stdout)
    print(result.stderr)

if __name__ == "__main__":
    run_java()
```

*Command:*
```
python3 runner.py
```

*Output:*
```
Exception in thread "main" java.io.FileNotFoundException: data.txt (No such file or directory)
    at java.base/java.io.FileInputStream.open0(Native Method)
    at java.base/java.io.FileInputStream.open(FileInputStream.java:219)
    at java.base/java.io.FileInputStream.<init>(FileInputStream.java:157)
    at java.base/java.io.FileReader.<init>(FileReader.java:58)
    at DataProcessor.main(DataProcessor.java:6)
```

---
TA Response 
---

 After looking over your code, i'm seeing that your java program is not finding the data.txt file. This could be due to the current working directory when the Java program is executed from the Python script. I recommend trying to modify the runner.py file to print the current working directory before and after running the Java program.

Add these lines to your script:
```
import os

def run_java():
    print("Current working directory before compiling:", os.getcwd())
    subprocess.run(["javac", "DataProcessor.java"])
    print("Current working directory before running:", os.getcwd())
    result = subprocess.run(["java", "DataProcessor"], capture_output=True, text=True)
    print(result.stdout)
    print(result.stderr)

if __name__ == "__main__":
    run_java()
```
--- 
Student Reply
---

I adjusted my code and ran it. This is the new output. 
```
Current working directory before compiling: /home/user/project
Current working directory before running: /home/user/project
Exception in thread "main" java.io.FileNotFoundException: data.txt (No such file or directory)
    at java.base/java.io.FileInputStream.open0(Native Method)
    at java.base/java.io.FileInputStream.open(FileInputStream.java:219)
    at java.base/java.io.FileInputStream.<init>(FileInputStream.java:157)
    at java.base/java.io.FileReader.<init>(FileReader.java:58)
    at DataProcessor.main(DataProcessor.java:6)
```
Bug:
The working directory is correct, but the Java program still cannot find data.txt. This suggests the problem might be related to how the Java program locates the file when run via the Python script.

All of the codes and commands stay the same except for the python snippet that was provided by the TA.

This is the new code snippet:
```
import subprocess
import os

def run_java():
    print("Current working directory before compiling:", os.getcwd())
    subprocess.run(["javac", "DataProcessor.java"])
    print("Current working directory before running:", os.getcwd())
    result = subprocess.run(["java", "DataProcessor"], capture_output=True, text=True)
    print(result.stdout)
    print(result.stderr)

if __name__ == "__main__":
    run_java()
```

The issue is how the java runtime locates the working directory when invoked from the Python script. To make sure that the `data.txt` file is found we must modify `runner.py`. We have to set the java runtimes working directory explicitly using the `cwd` parameter in the `subproess.run`.  

---
#Part 2#
---

I really enjoyed learning about Vim during the second half of the quarter. I also learned the importance of learning how to use lab machines and my personal machine because I've been having some trouble with the skill demos because I'm not used lab machines. The skill demos have been pretty challenging but have been a good way to practice and prove my skills. 
