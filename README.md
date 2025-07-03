# ROS Documentation

##  1.1 What is ROS?

ROS is nothing but an interface to simplify how components talk with each other. It can be thought of simply as a system of conventions which one can use to incorporate different sensors, motors, encoders and pretty much anything.
Let's dive into how it actually is useful for us. There are topics in ROS, on which data can be published by a program. The topic can then be subscribed by another program to get the data over there. These programs can be run on different machines in order to transfer data between them i.e. one device which has a program running on it which publishes to a specific topic, and another device, on the same network, has a program running on it that subscribes to the same topic, and receives data when it is published. These programs are called ROS Nodes. This, along with further terminology, will be explained further in this document.
## 1.2 Basic Terminology of ROS
### 1.2.1 ROS Node

StackEdit stores your files in your browser, which means all your files are automatically saved locally and are accessible **offline!**

## 1.3 Getting Started
### Installing ROS
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
