Sandbox for Spark-Notebook
================================

# Introduction

Vagrant project to spin up a cluster of 1 virtual machine with Hadoop v2.6.0, Spark v1.4.1 and Spark-Notebook 0.6.0

* [Hadoop](http://hadoop.apache.org)
* [Spark](http://spark.apache.org)
* [Spark-Notebook](https://github.com/andypetrella/spark-notebook)

# Getting Started

1. [Download and install VirtualBox](https://www.virtualbox.org/wiki/Downloads)
2. [Download and install Vagrant](http://www.vagrantup.com/downloads.html).
3. Run ```vagrant box add centos65 https://github.com/2creatives/vagrant-centos/releases/download/v6.5.1/centos65-x86_64-20131205.box```
4. Git clone this project, and change directory (cd) into this project (directory).
5. Run ```vagrant up``` to create the VM.
6. Run ```vagrant ssh``` to get into your VM.
7. Run ```vagrant destroy``` when you want to destroy and get rid of the VM.

Some gotcha's.

1. Make sure you download Vagrant v1.4.3 or higher.
2. Make sure when you clone this project, you preserve the Unix/OSX end-of-line (EOL) characters. The scripts will fail with Windows EOL characters.
3. Make sure you have 4Gb of free memory for the VM. You may change the Vagrantfile to specify smaller memory requirements.
4. This project has NOT been tested with the VMWare provider for Vagrant.
5. You may change the script (common.sh) to point to a different location for Hadoop and Spark to be downloaded from. Here is a list of mirrors for Hadoop: http://www.apache.org/dyn/closer.cgi/hadoop/common/.
6. Basically, Hadoop YARN is installed, but not started. If you want YARN Service, uncomment YARN section of `scripts/init-start-all-services.sh` and `scripts/start-all-services.sh`.

# Advanced Stuff

If you have the resources (CPU + Disk Space + Memory), you may modify Vagrantfile to have even more HDFS DataNodes, YARN NodeManagers, and Spark slaves. Just find the line that says "numNodes = 4" in Vagrantfile and increase that number. The scripts should dynamically provision the additional slaves for you.

# Make the VMs setup faster
You can make the VM setup even faster if you pre-download the Hadoop, Spark, and Oracle JDK into the /resources directory.

1. /resources/hadoop-2.6.0.tar.gz
2. /resources/spark-1.4.1-bin-hadoop2.tgz
3. /resources/jdk-7u51-linux-x64.gz
4. /resources/spark-notebook-0.6.0..tgz

The setup script will automatically detect if these files (with precisely the same names) exist and use them instead. If you are using slightly different versions, you will have to modify the script accordingly.

# Web UI
You can check the following URLs to monitor the Hadoop daemons.

1. [NameNode] (http://10.10.10.101:50070/dfshealth.html)
2. [Spark] (http://10.10.10.101:8080)
3. [Spark History] (http://10.10.10.101:18080)
4. [Spark-Notebook] (http://10.10.10.101:8989)

# Vagrant box location
The Vagrant box is downloaded to the ~/.vagrant.d/boxes directory. On Windows, this is C:/Users/{your-username}/.vagrant.d/boxes.

# Acknowledgements

This project is started from Jee Vang's [vagrant-hadoop-2.4.1-spark-1.0.1](https://github.com/vangj/vagrant-hadoop-2.4.1-spark-1.0.1). Thanks a lot.

# License
Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
