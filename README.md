

# Word Count Program using Hadoop MapReduce

## 📌 Description
This program counts the occurrences of each word in a given text document using Hadoop's MapReduce framework.

---

## 🛠 Prerequisites
- Java 8 or later  
- Hadoop installed and configured  
- HDFS running  

---

## 📂 Input
A text file containing multiple words. Below is the **exact input text** based on the output shown in the image:

```
hadoop harshita java mapreduce
```

---

## 📌 Steps to Run

### 1️⃣ Start Hadoop Services
Start the necessary Hadoop daemons required to run HDFS and MapReduce:
```sh
start-dfs.sh
start-yarn.sh
jps  # Verify that NameNode, DataNode, JobTracker, TaskTracker are running
```

---

### 2️⃣ Create Project Directory and Java Program
Navigate to your Hadoop workspace:
```sh
mkdir ~/hadoop-wordcount
cd ~/hadoop-wordcount
nano WordCount.java
```
Paste the Java MapReduce code into `WordCount.java` and save the file.

---

### 3️⃣ Compile the Java Program
```sh
hadoop com.sun.tools.javac.Main WordCount.java
jar cf wc.jar WordCount*.class
```

---

### 4️⃣ Create Input Directory in HDFS
```sh
hadoop fs -mkdir /input
```

---

### 5️⃣ Upload Input File to HDFS
Create a text file with the required input:
```sh
nano input.txt
```
Add the following content:
```
hadoop harshita java mapreduce
```
Save and exit, then upload it to HDFS:
```sh
hadoop fs -put input.txt /input/
hadoop fs -ls /input
```

---

### 6️⃣ Run the Hadoop MapReduce Job
```sh
hadoop jar wc.jar WordCount /input /output
```

---

### 7️⃣ **View the Output**
```sh
hadoop fs -cat /output/part-r-00000
```

---

## 📌  Output
Below is the  output:

```
hadoop      1
harshita    1
java        1
mapreduce   1
```

Each word in the input appears once, so the word count for each is **1**.

---


---

## ✅ Cleanup (Optional)
To remove previous output before running again:
```sh
hadoop fs -rm -r /output
```

---

## 📌 Conclusion
This document covers essential  HDFS commands and MapReduce Word Count execution in Hadoop. It provides a step-by-step guide to uploading files, executing MapReduce jobs, retrieving results, and managing HDFS directories. Understanding these commands and processes is crucial for effectively working with Hadoop's distributed computing framework. 🚀  

