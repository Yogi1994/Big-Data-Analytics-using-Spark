# Big-Data-Analytics-using-Spark


### Installation

    This class will use python3 not python2.
    The easiest way to install everything is to use the Docker instance that we provide. If for whatever reason, you cannot install Docker then we also provide instructions to download and install the required Python implementation and associated libaries.
    If you're a verified learner, then it's up to you to decide if you want to have a local development environment. We will provide you with a cloud hosted jupyter notebook interface for some of the Programming Assignments where you can code directly. We still recommend verified learners to setup the local environment anyhow.
    If you're auditing the course, then you should follow the instructions below. We highly recommend setting up using docker.

### Setup Using Docker

The purpose of this part is to ensure you have a working and compatible Python and PySpark installation. In order to avoid potential compatibility issues generated from students using different versions than the expected, we provide a Docker image with Ubuntu 16.04 and a clean Anaconda 4.3 with python 3.6, jupyter 5.4, spark 2.2 installation. We also provide a script to run the docker image and get Jupyter running on it so that you can program on it directly.

In this guide, we provide instructions on how to install Docker and pull the Docker image. In case you are not able to use Docker, you will have to install Python and Pyspark manually.

- Warning! Read Carefully

    Using the provided Docker container requires installing Docker, 6-7 GB of free space and root access on the host machine (admin rights for windows).
    If you are not able to use the provided container, you can install Python and Pyspark on your own. Make sure you follow the instructions given below. We will expect your results to match ours.
    Docker containers are not intended to store data. We highly recommend you develop your solutions locally and only use docker to compile and run. The following guides show you how to do that. Obtained results should be stored locally as well. If you develop within the container you are at risk of losing your work. You have been warned.
    When you work within the provided container (interactively or not) you are automatically logged in as a user named ucsddse230. Your homework notebook is mounted in the directory /home/ucsddse230/work. If you delete the mounted directory containing your work it will be deleted from the host system. Make sure your work is secure at all times. We recommend you use some sort of version control such as git.

### Installing Docker

Installing Docker should be straightforward for Windows and Mac OS users. Mac and Windows users can download it from from the Docker website.

Linux users will have to use this guide. The linux guides essentially try to upgrade your system to a compatible version (for example upgrading to Ubuntu 16.04). Be careful not to break your current system. If you are working with linux, having a Ubuntu 16.04 system should result in an easier docker installation.

For Windows users, Docker will require you enable Hyper-V and restart your computer. Some Windows 10 versions do not have Hyper-V. If you face any issues with installing Docker on Windows, installing Docker Toolbox instead of Docker should be the easiest way out.
Pulling the Docker image

After successful installation of Docker, open a command prompt or shell and execute the following command (Windows users should skip the “sudo” part): Linux/Mac:

```$ sudo docker pull ucsddse230/cse255-dse230```

Windows (Powershell prefered):

```$ docker pull ucsddse230/cse255-dse230```

Docker should automatically start downloading and extracting the provided image. If you skip this step the image will automatically be downloaded the first time you attempt to start it. Once finished you can verify you have it by typing Linux/Mac:

```$ sudo docker images```

Windows:

```$ docker images```

Students using Docker Toolbox for their Windows OS that does not support Hyper-V would now need to execute an additional command to identify their Docker IP address.

```$ docker-machine ip```

Note down the IP address that is returned as the output. You will need to use this in the next section.
Running Docker Images

Next, download the required content (for example, Programming assignment or Section Notebooks) files from EdX directory to some location on your computer. ex: /local/path/to/pa1

An an illustration, let's use Programming Assignment 1. You may open the Programming Assignment 1 section on EdX which has the link to the necessary started code.

Let's say after unpacking the files pa1 files are present in  /local/path/to/pa1

NOTE: This path should be the absolute path.

Then run the following following line of code in your terminal (first time might take a while).

```$ docker run -it -p 8889:8888 -v /local/path/to/pa1:/home/ucsddse230/work ucsddse230/cse255-dse230 /bin/bash```

This command will:

1. Start the docker container

2. mount the local directory "/local/path/to/pa1" inside the container at the location "/home/ucsddse230/work"

3. Forward requests to port 8889 on the local system from port 8888 inside the docker container.

Notice the terminal has changed, you are now inside a virtual machine. Run the following commands to start jupyter at `http://localhost:8889` by issuing the command

$ jupyter notebook

This will start jupyter at port 8888 inside the docker container, which will be accessible outside the docker at port 8889.

Now you can view notebooks and work on homework at the localhost:8889 port. Go ahead open your web browser and put "localhost:8889" in the address bar. You should now be able to see the Jupyter Notebook webpage.

Students using Docker Toolbox can access the Jupyter notebook running in their Docker container at the DockerIP:8888 port, where DockerIP is the IP address returned in the previous section.

Whatever changes you make will also happen to `/local/path/to/pa1`. 

Setup From Scratch

First install the Python 3.6 version using the anaconda distribution.
Install jupyter

If you install Anaconda, jupyter and almost all the necessary packages are installed for you.
Install notebook extensions

This step is not required, but extensions can make your work on notebooks significantly easier.

To install a bunch of useful extensions, together with a configurator for managing thses extensions, follow the directions on:

https://github.com/Jupyter-contrib/jupyter_nbextensions_configurator
Install python packages

Make sure to install the python package findspark. The typing the following command in the terminal installs the package:

  Anaconda:
  ```conda install -c conda-forge findspark=1.0.0```
  
  pip:
  ```sudo pip install findspark```

If you are using pip instead of anaconda, you also must install the following packages:

    numpy
    matplotlib

    pandas
    Some notebooks require additional packages, or packages of a later version. If an import command in a notebook fails, use pip or conda to install the missing package.

Install Spark on your computer

    Install on Linux or Mac OS X
    Install on Windows

