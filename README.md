
# ROS Documentation

##  1.1 What is ROS?

ROS is nothing but an interface to simplify how components talk with each other. It can be thought of simply as a system of conventions which one can use to incorporate different sensors, motors, encoders and pretty much anything.
Let's dive into how it actually is useful for us. There are topics in ROS, on which data can be published by a program. The topic can then be subscribed by another program to get the data over there. These programs can be run on different machines in order to transfer data between them i.e. one device which has a program running on it which publishes to a specific topic, and another device, on the same network, has a program running on it that subscribes to the same topic, and receives data when it is published. These programs are called ROS Nodes. This, along with further terminology, will be explained further in this document.
## 1.2 Basic Terminology of ROS
### 1.2.1 ROS Node
These are basically the programs that you code and run on a machine which is connected to the ROS server. It connects with the server to publish/subscribe to a topic. You can code it in different languages. Python and C++ are the most common ones.

### 1.2.2 ROS Master
You can think of this as the terminal which is running the server. When you start the ROS master, you start ROS, on which other ROS nodes and start subscribing/publishing to topics.

### 1.2.3 Launch files


## 1.3 Getting Started
### 1.3.1 Installing ROS
Before installing ROS, you need to understand what are the different versions of ROS. So, one thing that got me confused before was that ROS doesn't use numbers to indicate versions. Instead, it uses different names for it's versions. Please note that, by versions, I mean  versions for different OS's, different versions of those OS's. The right term used for versions regarding ROS is ***distributions***. The distribution that we will be using is ***ROS Noetic***. This is the distribution that is made for Ubuntu 20.04. Please note that, all along, in this document, Ubuntu 20.04 LTS would be used for everything.

Now, to install ROS, head on to the official [ROS Wiki](https://wiki.ros.org/noetic), and head to it's [installations page](https://wiki.ros.org/noetic/Installation). I will be linking everything, though it can be found, to make this a bit easy and encourage self exploration of the site. 
After selecting ubuntu from the installations page, follow it's steps. I'm also attaching all the commands here.

Update the sources list with the following command:

 ```sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'```
 
Now, if you wish to know what sources list mean here, just chatgpt it. There will be many things in this document that are out of the scope of it but good to know.
  
Install curl with the following command if not already installed:

```sudo apt install curl```

Moving on, set up the keys using the following command:

`curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | 
    sudo apt-key add`

Now, all the configurations before installing ROS are done, we can now proceed to install ROS.

First, make sure your Debian package index is up-to-date:
`sudo apt update`
Now, there are a couple of choices to install ros. Install the full package. This would include all the necesaary gui applications needed for development.
Install using the command:

`sudo apt install ros-noetic-desktop-full`

Finally, you would need to source a script in every bash terminal. What this means is that in order for your terminal to understand ros commands, you need to add one line in the file that stores all the commands of the terminal.
Instead of sourcing the script in every terminal, you could add it in the bashrc and forget about it.

`echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc`

`source ~/.bashrc`

With this done, ROS is installed on your computer. You can verify this by starting the ROS master. just run the following command in the terminal:

`roscore`

and there shouldn't be any errors.

You can now run pre-installed rosnodes to experiment. To run a ROS node, just use the following command:

`rosrun *nodename*`

One of the nodes which you can try running is the talker, by using the following command:

`rosrun rospy_tutorials talker`

On running this, the rosnode would start publishing.
To check all the ROS Nodes running and which one is publishing/subscribing to which topic, you can use the following command to see it as a mind map:

`rqt_graph`

You can write the name of the package with *rosrun* and press tab two times to get the list of all nodes present in the package, which you can run later.

### Note:
Now, you might have gotten a rough idea about how ros works and how to use it. One thing that i'd like to add(that might be already noticed, but for the sake of saying) is that when you make a ROS Node, you are essentially making a python/c++ program, which will be run. This means that you can do ***LITERALLY ANYTHING*** that can be done with a program. Be it interfacing with a sensor and publishing data on a topic, to subscribing to a topic and running a PID loop to make the motors go a certain way. The sky is the limit.

### 1.3.2 Making a Catkin Workspace

To make a workspace, let's first understand what is a workspace. A workspace is nothing but a convention of naming folders and storing programs in it that makes it easy for other users to read. It's basically like commenting in a program, which makes it structured.

For ROS, we use a ***Catkin Workspace***. For now, you can think of catkin as a build system, which helps compile and manage all the rosnodes easily.

To create a catkin workspace, run the following command in terminal in the home folder:

`mkdir catkin_ws/`

Then, go inside the folder by using:

`cd catkin_ws/`

Now, make(build) the workspace by

`catkin_make`

With this, your workspace is ready to be used.

The file structure would look something like this:

```
catkin_ws/ # Root directory of your workspace (name can vary)  
├── src/ # Source space: contains all your ROS packages 
├── build/ # Build space: generated after building (contains build files)  
├── devel/ # Development space: built packages are linked here  
└── install/ # Install space (only if using catkin_make install)```
