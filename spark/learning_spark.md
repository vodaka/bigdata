# 1 Introduction to Core Spark Concepts
At a high level, every spark application consist of a  *driver program* that launches various parallel operations on a cluster. The drive program container your application's main funciton and defines distributed datasets on the cluster, then applies operation to them.
Driver programs access spark through a SparkContext obeject, which represents a connection to a computing cluster.In the shekk , a SparkContext is a automatically created for you as the variable called sc.
Once you have a SparkContext , you can use it to build RDDs.
## 1.1 Python Script
In Python ,you simly write applications as Python scripts , but you must run them using the bin/spark-submit script included in spark. The spark-submit script in the spark dependencies for us in Python. This script sets up the environment for spark's Python API to function.

`bin/spark-submit my_script.py`

## 1.2 Intializing a SparkContext
Once you have linked an application to Spark, you need to import the Spark packages in your program and create a SparkContext . You do so by first creating a SparkConf object to configure your application, and then building a SparkContext for it.

*Example Initializing Spark in Python*
