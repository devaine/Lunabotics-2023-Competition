# Development Branch for Lunabotics on Windows
## NOTICE: This is under the assumption that you installed the [Windows Version of ROS 2 (Humble)](https://docs.ros.org/en/humble/Installation/Windows-Install-Binary.html)

# Table of Cotents
1. [Tutorials and Refences](#tutorials--references)
2. [Packages Used](#external-packages-used)
3. [Notes](#notes)
4. [Notice for ```./ros2Setup.bat```](#notice-for-ros2setupbat)
5. [Defining Directories & Setting Up Build Environment](#defining-directories-and-setting-up-build-environment)
6. [Packages](#packages)

## Basic Diagram for interactions between hardware components
![Diagram](./images/Diagram.png)

## Tutorials & References
- [ROS2 Humble Windows Binary Install](https://docs.ros.org/en/humble/Installation/Windows-Install-Binary.html)
- [Wiki for ROS2 Tutorials on Humble](https://docs.ros.org/en/humble/Tutorials.html)
- [What are nodes?](https://docs.ros.org/en/humble/Tutorials/Beginner-CLI-Tools/Understanding-ROS2-Nodes/Understanding-ROS2-Nodes.html)
- [Building Packages with Colcon](https://docs.ros.org/en/humble/Tutorials/Beginner-Client-Libraries/Colcon-Tutorial.html)
- [Create your own package](https://www.ros.org/reps/rep-0140.html)
- [Creating Packages](https://docs.ros.org/en/humble/Tutorials/Beginner-Client-Libraries/Colcon-Tutorial.html)
- [Example for creating nodes](https://github.com/ros2/demos/tree/humble/demo_nodes_cpp)
- [The ROS_DOMAIN_ID](https://docs.ros.org/en/humble/Concepts/Intermediate/About-Domain-ID.html)
    - [Domain ID to UDP Port Calculator](https://docs.ros.org/en/humble/Concepts/Intermediate/About-Domain-ID.html#domain-id-to-udp-port-calculator)


## External Packages Used
- 

---
# Notes:

## Notice for ```./ros2Setup.bat```
If you want to use <code>./ros2Setup.bat</code>, make sure you're executing that on Command Prompt:
* Also, <code>./ros2Setup.bat</code> is set for a specific path on my device, make sure it fits for your own path to the ros2 <code>local_setup.bat</code>.
* If you wish to use the powershell script, I suggest looking at [this.](https:\go.microsoft.com\fwlink\?LinkID=135170) if you care about your computer's permissions.

## Defining Directories and Setting Up Build Environment
```src/``` => Where your ROS 2 Source code is.
    - ```colcon``` (when executed) will create directories => <code>build/</code>,<code>install/</code>, and <code>log/</code>.
* To build ROS2 code, use the VS2019 envionment by searching up in your Start Menu...

<pre>x64 Native Tools Command Prompt for VS 2019</pre>

1. Make sure you have environment variables set for an Administrator (CMake, Python, and Python Scripts)
2. And execute your ROS2 setup executable beforehand in order to build
    - [use this for setuptools if there's an error for "setup.py"](https://answers.ros.org/question/396439/setuptoolsdeprecationwarning-setuppy-install-is-deprecated-use-build-and-pip-and-other-standards-based-tools/) [and this too if you're still stuck](https://www.reddit.com/r/ROS/comments/wxkfes/colcon_build_failed_in_example_failed_examples/)
    - From what's shown, <code>package.xml</code> is meant to be within a package directory under <code>src/</code>
    - **REQUIRED**: When starting a new terminal instance or when you're building/executing code, make sure your ROS2 is *sourced* before doing executing any ```colcon``` or ```ros2``` commands

## Packages
### What is a package?
- A package is a organizational unit for ROS 2 code. It helps with installing and sharing code.
- Uses <code>ament</code> as it's build system and <code>colcon</code> as it's build tool.
- Creating a package only works with colcon and/or Python

### Contents of a Package
- <code>CMakeLists.txt</code> describes how to build the code.
- <code>include/<i>package_name/</i></code> contains the headers for the package.
- <code>package.xml</code> contains information about the package.
- <code>src/</code> contains the source code.

### Workspaces
- Workspaces can contain multiple packages (each in their own folder)
    - They can also can contain packages of any type within.
- You cannot have nested packages in a workspace.
- The best practice is to have have <code>./src></code> folder <i>within</i> your workspace and put your packages in there.

- <b>Remember!</b> if you want to build multiple packages at once, you can use <code>colcon build</code> in the workspace root directory. (not <code>./src</code> but rather the directory above it.)
    - You can also use <code>colcon build</code> for building invdividual packages, just makes sure you're in the package's directory.
    - If you wish to <i>select</i> a package to build from colcon, you can use (in the root directory):
    <pre>colcon build --packages-select <i>package</i></pre>

### Steps in order to create a new package + workspace
1. Create your workspace (create a new folder)
2. Source your ROS 2 install setup <code>./ros2Setup.bat</code>
3. Create your package 
    - You may use the command (creates a package + a empty node inside the package)
    <pre>ros2 pkg create --build-type ament_cmake --license Apache-2.0 --node-name <i>my_node</i> <i>my_package</i></pre>

    **OR**

    - You can create your own directory with:
        - ```package.xml``` - You may use ```./xmltemplate.txt```
        - ```CMakeLists.txt``` (if you know how to use CMake you can modify it to your liking.)
        - a ```LICENSE``` of your choice (sprcify in ```package.xml``` too)
        - ```src/``` directory for your node source code.
    - Program code for the node in ```src/``` and build it
4. Execute your code by executing in the root directory of your workspace:
<pre>colcon build</pre>

5. You can run the program by specifying the node and the package by using:
<pre>ros2 run <i>my_package</i> <i>my_node</i> </pre>

### Nodes
- Are executables that communicate over ROS graph, they pass information (in the form of string messages over a **topic**)
 
### Nodes and Domain ID's
- Use ```ROS_DOMAIN_ID``` environment variable to 'gorup up' nodes in order to differentiate which nodes are meant to do something than other nodes doing something else.
    - The default domain value for all nodes in ROS 2 is ```0```, however you could change that by firstly declaring what domain value ```ROS_DOMAIN_ID``` should be by typing:
    <pre> set ROS_DOMAIN_ID = <i>value</i></pre>
    -  [Although I do suggest that you should limit your value from ```0-101```](https://docs.ros.org/en/humble/Concepts/Intermediate/About-Domain-ID.html#platform-specific-constraintsI30@">DfhfN!s5)