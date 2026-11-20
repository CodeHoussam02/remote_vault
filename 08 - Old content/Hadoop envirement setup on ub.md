
**useful medium blog**  [[Install Hadoop on Ubuntu Operating System | by Code With Arjun | Medium](https://codewitharjun.medium.com/install-hadoop-on-ubuntu-operating-system-6e0ca4ef9689)]

# 1. Pre-requisites 

1. create a hadoop user 

- create user 

```bash
sudo addgroup hadoop
```

- add the hduser to hadoop group 

```bash 
sudo adduser --ingroup hadoop hduser
```

- give the hduser root privillage 

```bash 
sudi visudo 

hduser ALL=(ALL:ALL) ALL
```

3. first of all you need to install the openJDK which is the main key for hadoop to run on your machine 

- you can check before if java is already installed by this command 

```bash 
java --version
```

- it preferred to install java in `usr/local` directory so you gonna need to switch to this directory

```bash 
cd /usr/local
```

- if not installed you can use this link : https://download.oracle.com/java/23/latest/jdk-23_linux-x64_bin.tar.gz

```bash 
sudo wget https://download.oracle.com/java/23/latest/jdk-23_linux-x64_bin.tar.gz
```

- after you will need to unzip it 

```bash 
sudo tar -xvzf file_name
```

- rename the created folder to `java` by this command `sudo mv JDk-.. java`

### or you can install java by running this command 

```bash 
sudo apt install openjdk-8-jdk 
```

- check java version

```bash 
java -version
```

- we need to set up our environment variables in the `~/.bashrc` file

```bash 
export JAVA_HOME = 'location' -> /usr/local/java
export PATH = $PATH:/usr/local/java/bin
```

- **NOTE** : the bin file contains all the java executables.

- Now we need to set the alternatives to make java able to identify java, javac and all the stuff

1. first command : 

```bash
sudo update-alternatives --install "/usr/bin/java" "java" "/usr/local/java/bin/java" 1
```

2. Second command 

```bash 
sudo update-alternatives --install "/usr/bin/javac" "javac" "/usr/local/java/bin/javac" 1
```

3. Third command 

```bash 
sudo update-alternatives --install "/usr/bin/javaws" "javaws" "/usr/local/java/bin/javaws" 1
```

- After executing the commands above we need to execute these three commands 

```bash 
sudo update-alternatives --set java /usr/local/java/bin/java
sudo update-alternatives --set javac /usr/local/java/bin/javac
sudo update-alternatives --set javaws /usr/local/java/bin/javaws
```


# ssh key

- because hadoop uses ssh to communicate between its different components we need to find a way to escape the password check because it's gonna cause a problem in this case 
- for this reason we gonna generate a key that will be add to each node server, so that when ever a node tries to communicate to another it will check only the `security key`

- How to generate a secret-key : 

```bash 
ssh-keygen -t rsa 
```

- in order to view the key 

```bash 
cat ~/.ssh/id_rsa.pub
```

- after we need to add our secret-key to the ssh-authorized file 

```bash
cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_key
```


# 2. Hadoop installation & configuration 

- you need to go to the official ==***hadoop==*** website to install it : [Apache Hadoop](https://hadoop.apache.org/releases.html)

- then you install the latest version : https://dlcdn.apache.org/hadoop/common/hadoop-3.4.1/hadoop-3.4.1.tar.gz

- extract the data from the archive file 
- now we need to set full permissions to the hduser on the hadoop directory and become its owner as well 

```bash 
# first command 
sudo chown -R hduser:hadoop /usr/local/hadoop/
# Second command for full execution privillage
sudo chmod -R 777 /usr/local/hadoop/
```

- before installing hadoop we need to disable IPv6 in `/stc/sysctl.conf`

```bash
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
```

- configuration of `~/.bashrc` file 

```bash 
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
```

- you need to add some lines in bashrc configuration files 

```bash 
export HADOOP_HOME=/usr/local/hadoop
export HADOOP_CONF_DIR=/usr/local/hadoop/etc/hadoop
export HADOOP_MAPRED_HOME=/usr/local/hadoop
export HADOOP_COMMON_HOME=/usr/local/hadoop
export HADOOP_HDFS_HOME=/usr/local/hadoop
export YARN_HOME=/usr/local/hadoop
export PATH=$PATH:/usr/local/hadoop/bin
export PATH=$PATH:/usr/local/hadoop/sbin

export HADOOP_COMMON_LIB_NATIVE_DIR=$HADOOP_HOME/lib/native
export HADOOP_OPTS=".Djava.library.path=$HADOOP_HOME/lib"
```

- now its time to configure some configuration files in order to make hadoop ready for work
	1. `hadoop-env.sh` : this file is the first file that gets executed when you fire up your namenode or hadoop cluster
	
```bash
export HADOOP_OPTS=-Djava.net.preferIPv4Stack=true
export JAVA_HOME=/usr/local/java
export HADOOP_HOME_WARN_SUPPRESS="TRUE"
export HADOOP_ROOT_LOGGER="WARN,DRFA"
```

	2. configure YARN : 

```bash 
export HADOOP_OPTS=-Djava.net.preferIPv4Stack=true
export JAVA_HOME=/usr/local/java
export HADOOP_HOME_WARN_SUPPRESS="TRUE"
export HADOOP_ROOT_LOGGER="WARN,DRFA"
```

	3. core-site.xml : 

```xml
<configuration>  
	<property>  
		<name>fs.defaultFS</name>  
		<value>hdfs://localhost:9000</value> 
	</property>  
	<property>  
		<name>hadoop.proxyuser.dataflair.groups</name> 
		<value>*</value>  
	</property>  
	<property>  
		<name>hadoop.proxyuser.dataflair.hosts</name> <value>*</value>  
	</property>  
	<property>  
		<name>hadoop.proxyuser.server.hosts</name> <value>*</value>  
	</property>  
	<property>  
		<name>hadoop.proxyuser.server.groups</name> <value>*</value>  
	</property>  
</configuration>
```

	4. mapred-site.xml 

```bash 
```

- create some useful directories 

we need to give the full permission access to the hadoop directory

```bash
sudo chmod 777 -R /usr/local/hadoop/**
```

- temp dir 

```bash 
sudo mkdir -p /app/hadoop/tmp

# and after we give the hduser the ownership over this file 

sudo chown -R hduser:hadoop /app/hadoop/tmp
sudo chmod -R 777 /app/hadoop/tmp
```

- namenode directory 

```bash
sudo mkdir -p /usr/local/hadoop/yarn_data/hdfs/namenode
 
sudo chmod -R 777 /usr/local/hadoop/yarn_data/hdfs/namenode/

sudo chown -R hduser:hadoop /usr/local/hadoop/yarn_data/hdfs/namenode/
```

- datanode directory

```bash
sudo mkdir -p /usr/local/hadoop/yarn_data/hdfs/datanode

sudo chmod -R 777 /usr/local/hadoop/yarn_data/hdfs/datanode/

sudo chown -R hduser:hadoop /usr/local/hadoop/yarn_data/hdfs/datanode/
```


---


# test hadoop

```bash 
hadoop version 

javac -version
```


# Hadoop commands 


- inisiate namenode

```bash 
hdfs namenode -format
```

- visualise or list running processies on java virtual machine 

```bash 
jps
```

- start all daemons

```bash 
# start all
start-all.sh
# stop all 
stop-all.sh
```

- access namenode

```
localhost:9870
```

- cluster info 

```
localhost:8042
```

- yarn (hadoop nodes)

```
localhost:9864
```


# hdfs commands 

- create a new directory

```bash 
hdfs dfs -mkdir /Folder_one
```

- hdfs command to remove a directory 

```bash
hdfs dfs -rm -r /directory
```