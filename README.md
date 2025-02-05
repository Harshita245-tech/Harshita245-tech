# Word Count Program using Hadoop MapReduce

## 📌 Description
This program counts the occurrences of each word in a given text document using Hadoop's MapReduce framework.

## 🛠 Prerequisites
- Java 8 or later
- Hadoop installed and configured
- HDFS running

## 📂 Input
A text file containing multiple words. Example:
```
hadoop is great
hadoop is scalable
hadoop is fast
```

## 📌 Steps to Run

### 1️⃣ Setup Hadoop Environment
Ensure Hadoop is running:
```sh
start-dfs.sh
start-yarn.sh
jps  # Verify services like NameNode, DataNode, JobTracker, TaskTracker are running
```

### 2️⃣ Create Project Directory and Java Program
Navigate to your Hadoop workspace:
```sh
mkdir ~/hadoop-wordcount
cd ~/hadoop-wordcount
nano WordCount.java
```
Paste the Java MapReduce code into `WordCount.java` and save the file.

### 3️⃣ Compile the Java Program
```sh
hadoop com.sun.tools.javac.Main WordCount.java
jar cf wc.jar WordCount*.class
```

### 4️⃣ Create Input Directory in HDFS
```sh
hadoop fs -mkdir /input
```

### 5️⃣ Upload Input File to HDFS
Create a text file with sample data:
```sh
nano input.txt
```
Add the following content:
```
hadoop is great
hadoop is scalable
hadoop is fast
```
Save and exit, then upload it to HDFS:
```sh
hadoop fs -put input.txt /input/
hadoop fs -ls /input
```

### 6️⃣ Run the Hadoop MapReduce Job
```sh
hadoop jar wc.jar WordCount /input /output
```

### 7️⃣ View the Output
```sh
hadoop fs -cat /output/part-r-00000
```
Expected Output:
```
hadoop    3
is        3
great     1
scalable  1
fast      1
```

## 📝 Assumptions
- Words are case-insensitive (converted to lowercase).
- Words are separated by spaces.
- Punctuation is not handled.

## ✅ Cleanup (Optional)
To remove previous output before running again:
```sh
hadoop fs -rm -r /output
```

