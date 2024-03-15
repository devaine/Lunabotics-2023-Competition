# Development Branch for Lunabotics on Windows
## NOTICE: This is under the assumption that you installed the [Windows Version of ROS 2 (Humble)](https://docs.ros.org/en/humble/Installation/Windows-Install-Binary.html)

## Table of Contents
1. [Tutorials and Refences](#tutorials--references)
2. [Packages Used](./Notes.md/#external-packages-used)
3. [The Checklist](#the-checklist)
4. [Notes](Notes.md/#notes)
    * [Notice for ```./ros2Setup.bat```](./Notes.md/#notice-for-ros2setupbat)
    * [Defining Directories & Setting Up Build Environment](./Notes.md/#defining-directories-and-setting-up-build-environment)
5. [Packages](./Notes.md/#packages)
    * [What's a package?](./Notes.md/#what-is-a-package)
    * [The contents of a package](./Notes.md/#contents-of-a-package)
    * [Create a package manually](./Notes.md/#steps-in-order-to-create-a-new-package--workspace)
6. [Workspaces](./Notes.md/#workspaces)
7. [The ROS Graph](./Notes/#the-ros-graph)
8. [Nodes](./Notes.md/#nodes)
    * [The Functionality of Nodes](./Notes.md/#the-functionality-of-nodes)
    * [Commands for Nodes](./Notes.md/#commands-for-nodes)
    * [Nodes & Domain ID's](./Notes.md/#nodes-and-domain-ids)

## Basic Diagram for interactions between hardware components
![Diagram](./images/Diagram.png)


## External Packages Used
- [```joy```](https://index.ros.org/p/joy/) - Interfaces a generic joystick to ROS 2


## The Checklist
- [X] Install ROS 2 on Windows
- [X] Setup Coding Environment by setting programs to PATH

- [ ] Learning Phase
    - [X] Learn about Packages
    - [X] Learn about Nodes
    - [ ] Learn about Topics
    - [ ] Learn about Actions

- [X] Find a package that'll help with coding for the controller
    - [ ] Setup controller declaration in code
    - [ ] Print out controller input in Laptop for proof of concept
    - [ ] Send controller input to Raspberry Pi
    - [ ] Print out results from Raspberry Pi
    - [ ] Use controller input to send to another node