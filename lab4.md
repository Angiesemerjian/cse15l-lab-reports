# Step 4 #
```
ssh <space> asemerjian@ieng6.ucsd.edu
<enter>
```
![Image](Screen Shot 2024-05-22 at 4.58.51 PM.png)
# Step 5 #
```
<Command-C>
git <space> clone <space> <Command-V> <space>git@github.com:Angiesemerjian/lab7.git`
<enter>
cd <space> lab7
<enter>
```
![Image](Screen Shot 2024-05-22 at 5.02.07 PM.png)
![Image](Screen Shot 2024-05-22 at 5.06.31 PM.png)

# Step 6 # 

```
<up>, <enter>
```
The `javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java` command was one up in the history. 

```
command-C, command-V, <enter>
```
The `java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests` was copied and pasted. The commands are Command-C to copy and Command-V to paste. 

![Image](Screen Shot 2024-05-22 at 7.18.52 PM.png)

# Step 7 # 

command:
`vim <space> ListExamples.java`
```
<down> x50
i
delete, 2
esc
Shift :wq, <enter>
```
![Image](Screen Shot 2024-05-22 at 7.24.03 PM.png)

When you enter vim, you must use the down arrow to go to line 50, where index1+=1 is located. Then you must delete the 1 and change it to a 2, then save and exit. 

# Step 8 #

```
<up>,<up>, <enter>,<up>, <up>, <enter>
```
The command `javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java` was two up in the history. After compiling the files, I used the command `java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests`, which was also two up in the history. 

![Image](Screen Shot 2024-05-22 at 7.17.50 PM.png)

# Step 9 #
```
git <space> add . <enter>
git <space> commit <space> -m <space> "Fixed <space> Tests" <enter>
git <space> push <space> origin <space> main <enter>
```
![Image](Screen Shot 2024-05-22 at 7.26.46 PM.png)





