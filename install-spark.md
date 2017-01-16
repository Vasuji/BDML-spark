# info-Spark(java,scala,python,R,git)
![alt tag](http://spark.apache.org/images/spark-logo-trademark.png)

### EDX:Scalable Machine Learning

 - Oracle's Virtual Box
 - Vagrant automatic VM configuration
 - vagrant file (https://github.com/spark-mooc/mooc-setup/archive/master.zip)
 - Keep vagrant file in a separate folder
 - Go to that new folder
 - ``` vagrant up --provider=virtualbox ```
 - Next time ```vagrant up ``` to start and ```vagrant halt``` to end the machine
 - Go to http://localhost:8001

### Spark-setup ================================
Cloudera VM Spark-set up

#### Install IPython

From the top left menu, Open a terminal: Applications => System Tools => Terminal

Type:
```
sudo easy_install ipython==1.2.1
```
Hit enter, administrator password is cloudera.

###Launch pyspark with IPython

Every time you need to open the pyspark shell, open a terminal and type:
```
PYSPARK_DRIVER_PYTHON=ipython pyspark
```
Hit enter, after the startup logs, you should see the pyspark console:

Check version

To make sure that PySpark started correctly, print out the version by typing in the PySpark IPython terminal:
```
sc.version
```

Verify that the output is:
```
u'1.3.0'
```

### Spark -csv Installation link:

http://spark-packages.org/package/databricks/spark-csv

type in terminal

```
PYSPARK_DRIVER_PYTHON=ipython pyspark --packages com.databricks:spark-csv_2.10:1.3.0
```
============================================================================================
# Stand alone mode ============================
============================================================================================
1. Check java version 
    ```
    $java -version
    ```
 it will be like:
  ```
       java version "1.8.0_60"
       Java(TM) SE Runtime Environment (build 1.8.0_60-b27)
       Java HotSpot(TM) 64-Bit Server VM (build 25.60-b23, mixed mode)
  ```

2. Export java path:
     ```
       $export JAVA_HOME=$(/usr/libexec/java_home) 
     ```

3. Check wheteher you have brew installed or not:
 
    ```
        $which brew
        /usr/local/bin/brew

    ```
     if there is not brew, install it by:
     ```
       ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)" 
       ```

4. Install scala:
       ```
        brew install scala210
       ```

5. Download Spark and scala and unzip


6. Go to spark/conf/ and copy 'spark-env.sh-templet' to make 'spark-env.sh' and edit it
    ```
         export SCALA_HOME=/Users/dibakarsigdel/scala-2.10.6
         export PYSPARK_PYTHON=/Library/Frameworks/Python.framework/Versions/2.7/bin/python
    ```
    
7. Build and install spark
   ```
   sbt/sbt clean assembly
   ```
8. Fire up spark

```./bin/pyspark
   ./bin/spark-shell
   ./bin/spark-shell --packages com.databricks:spark-csv_2.10:1.3.0

```
9.  Enjoy!


==========================================================================
### Setup Ipython -Notebook for spark =====================
========================================================================
 - http://blog.cloudera.com/blog/2014/08/how-to-use-ipython-notebook-with-apache-spark/

 1 . First create an IPython profile for use with PySpark.

```
  ipython profile create pyspark
```
2 .  This should have created the profile directory ``` ~/.ipython/profile_pyspark/.```  Edit the file ```~/.ipython/profile_pyspark/ipython_notebook_config.py ``` to have:

```
c = get_config()
 
c.NotebookApp.ip = '*'
c.NotebookApp.open_browser = False
c.NotebookApp.port = 8880 # or whatever you want; be aware of conflicts with CDH
```

3 . Finally, create the file ```~/.ipython/profile_pyspark/startup/00-pyspark-setup.py```  with the following contents:

```
import os
import sys
 
spark_home = os.environ.get('SPARK_HOME', None)
  if not spark_home:
      raise ValueError('SPARK_HOME environment variable is not set')
sys.path.insert(0, os.path.join(spark_home, 'python'))
  sys.path.insert(0, os.path.join(spark_home, 'python/lib/py4j-0.8.1-src.zip'))
execfile(os.path.join(spark_home, 'python/pyspark/shell.py'))

```
5 . Run it and go to 'http://localhost:8880/'
   ```
     ipython notebook --profile=pyspark
   ```








#### Installation Links
 - ununtu: http://blog.prabeeshk.com/blog/2014/10/31/install-apache-spark-on-ubuntu-14-dot-04/
 - http://www.tutorialspoint.com/apache_spark/apache_spark_installation.htm
 - mac: http://genomegeek.blogspot.com/2014/11/how-to-install-apache-spark-on-mac-os-x.html
 - https://www.youtube.com/watch?v=eQ0nPdfVfc0

#### Tutorials Links
 - https://spark.apache.org/docs/1.3.0/sql-programming-guide.html
 - 
