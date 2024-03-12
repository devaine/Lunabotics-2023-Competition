# Development Branch for Lunabotics on Windows

## Basic Diagram for interactions between hardware components
![Diagram](./images/Diagram.png)

## Tutorials Used
- [ROS2 Humble Windows Binary Install](https://docs.ros.org/en/humble/Installation/Windows-Install-Binary.html)
- [Wiki for ROS2 Tutorials on Humble](https://docs.ros.org/en/humble/Tutorials.html)


---
# Notes:

If you want to use <code>./ros2Setup.bat</code>, make sure you're executing that on Command Prompt:
* Also, <code>./ros2Setup.bat</code> is set for a specific path on my device, make sure it fits for your own path to the ros2 <code>local_setup.bat</code>.

It's only temporary to the Powershell process you're using though. [For more information](https:\go.microsoft.com\fwlink\?LinkID=135170)

[Source Your ROS2 Setup Script](https://docs.ros.org/en/humble/Tutorials/Beginner-CLI-Tools/Configuring-ROS2-Environment.html#add-sourcing-to-your-shell-startup-script) is the source for <code>./ros2Setup.bat</code>

[What are nodes?](https://docs.ros.org/en/humble/Tutorials/Beginner-CLI-Tools/Understanding-ROS2-Nodes/Understanding-ROS2-Nodes.html)

[Building Packages with Colcon](https://docs.ros.org/en/humble/Tutorials/Beginner-Client-Libraries/Colcon-Tutorial.html)
## Notes
- src subdirectory = source code for ROS2 packages
    - colcon will create directories => <code>build</code>,<code>install</code>, and <code>log</code>.
- To build ROS2 code you can use ```colcon``` by using a VS2019 envionment by searching up in your start...
<pre>x64 Native Tools Command Prompt for VS 2019</pre>

- Make sure you have environment variables set for an Administrator (CMake, Python, and Python Scripts)
- And execute your ROS2 setup executable beforehand in order to build
- [use this for setuptools if there's an error for "setup.py"](https://answers.ros.org/question/396439/setuptoolsdeprecationwarning-setuppy-install-is-deprecated-use-build-and-pip-and-other-standards-based-tools/)
    - [and this too](https://www.reddit.com/r/ROS/comments/wxkfes/colcon_build_failed_in_example_failed_examples/)
- From what's shown, it seems that <code>package.xml</code> is meant to be within a package directory under <code>./src</code>

[Create your own package](https://www.ros.org/reps/rep-0140.html)


[Creating Packages](https://docs.ros.org/en/humble/Tutorials/Beginner-Client-Libraries/Colcon-Tutorial.html)
---
## Notes
- A package is a organizational unit for ROS 2 code. It helps with installing and sharing code.
- Uses <code>ament</code> as it's build system and <code>colcon</code> as it's build tool.
- Creating a package only works with colcon and Python

### Here's what makes a package
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
    - If you wish to <i>select</i> a package to build from colcon, you can use:
    <pre>colcon build --packages-select <i>package</i></pre>
    In the root directory

[Example for creating nodes](https://github.com/ros2/demos/tree/humble/demo_nodes_cpp)