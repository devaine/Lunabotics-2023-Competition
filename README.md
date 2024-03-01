# Development Branch for Lunabotics on Windows

## Basic Diagram for interactions between hardware components
![Diagram](./images/Diagram.png)

## Tutorials Used
- [ROS2 Humble Windows Binary Install](https://docs.ros.org/en/humble/Installation/Windows-Install-Binary.html)
- [Wiki for ROS2 Tutorials on Humble](https://docs.ros.org/en/humble/Tutorials.html)


---
# Notes:

If you want to use <code>./powershellSetup.ps1</code>, you can use this command:
<pre>Set-ExecutionPolicy -ExecutionPolicy Bypass -Scope Process</pre>
* Also, <code>./powershellSetup.ps1</code> is only setup through my laptop, just change the path to the <code>local_setup.ps1</code> to your <i>own</i> local path.

It's only temporary to the Powershell process you're using though. [For more information](https:\go.microsoft.com\fwlink\?LinkID=135170)

[Source Your ROS2 Setup Script](https://docs.ros.org/en/humble/Tutorials/Beginner-CLI-Tools/Configuring-ROS2-Environment.html#add-sourcing-to-your-shell-startup-script) is the source for <code>./powershellSetup.ps1</code>