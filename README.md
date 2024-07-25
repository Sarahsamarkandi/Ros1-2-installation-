# Ros1-2-installation-


---
For the smartmethods AI track the first task was install Ros 1 and Ros 2 and here<s the detailed method that i follow for the installation

### How I Installed VirtualBox, Ubuntu 20.04, ROS 1, and ROS 2

#### Step 1: Installing VirtualBox

1. **Downloading VirtualBox:**
   I visited the [VirtualBox download page](https://www.virtualbox.org/wiki/Downloads) and downloaded the installer for Windows.

2. **Installing VirtualBox:**
   I ran the installer and followed the prompts to complete the installation with default settings. 

3. **Starting VirtualBox:**
   After installation, I opened VirtualBox from the Start menu.
![Screenshot 2024-07-20 214313](https://github.com/user-attachments/assets/85c73ac8-3510-4f19-8521-c3851e376825)

#### Step 2: Setting Up Ubuntu 20.04 on VirtualBox

1. **Downloading Ubuntu 20.04 ISO:**
   I went to the [Ubuntu download page](https://ubuntu.com/download/desktop) and downloaded the Ubuntu 20.04 LTS ISO file.

2. **Creating a New Virtual Machine:**
   - I opened VirtualBox and clicked "New".
   - I named my virtual machine "Ubuntu 20.04", selected "Linux" as the type, and "Ubuntu (64-bit)" as the version.
   - I allocated 2048 MB of RAM (2 GB) to the virtual machine.
   - I created a new virtual hard disk, chose "VDI (VirtualBox Disk Image)", selected "Dynamically allocated", and set the size to 20 GB.

3. **Configuring the Virtual Machine:**
   - I selected my new virtual machine and clicked "Settings".
   - In the "Storage" section, I clicked the empty disk icon under "Controller: IDE", then clicked the disk icon next to "Optical Drive" and chose "Choose a disk file".
   - I selected the Ubuntu 20.04 ISO file I had downloaded.
   - In the "System" section, under the "Motherboard" tab, I unchecked "Floppy" in the Boot Order and moved "Optical" to the top.

4. **Installing Ubuntu:**
   - I clicked "Start" to boot the virtual machine.
   - I selected "Install Ubuntu" on the welcome screen.
   - I chose my language and clicked "Continue".
   - I selected my keyboard layout and clicked "Continue".
   - I chose "Normal installation", checked the options to install updates and third-party software, and clicked "Continue".
   - I chose "Erase disk and install Ubuntu" since it was a virtual machine.
   - I selected my time zone and clicked "Continue".
   - I entered my personal details, including name, computer name, username, and password, and clicked "Continue".
   - I waited for the installation to complete, then restarted the virtual machine when prompted.
![Screenshot 2024-07-23 031318](https://github.com/user-attachments/assets/f996c47d-00a5-4846-87b8-1032b8eb9d6b)
![Screenshot 2024-07-22 034015](https://github.com/user-attachments/assets/b9ed5508-6f90-48b6-b36e-30cf0a20b411)

#### Step 3: Installing ROS 1 (Noetic)

1. **Setting Up the Sources List:**
   - I opened a terminal in Ubuntu and entered:
     ```bash
     sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
     ```

2. **Setting Up the Keys:**
   - I entered the following command:
     ```bash
     sudo apt install curl -y
     curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
     ```

3. **Installing ROS Noetic:**
   - I updated the package list:
     ```bash
     sudo apt update
     ```
   - I installed ROS Noetic:
     ```bash
     sudo apt install ros-noetic-desktop-full
     ```

4. **Initializing rosdep:**
   - I entered the following commands:
     ```bash
     sudo apt install python3-rosdep
     sudo rosdep init
     rosdep update
     ```

5. **Setting Up the Environment:**
   - I added the following line to my `.bashrc`:
     ```bash
     echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
     source ~/.bashrc
     ```

6. **Installing Dependencies for Building Packages:**
   - I installed the following:
     ```bash
     sudo apt install python3-rosinstall python3-rosinstall-generator python3-wstool build-essential
     ```

#### Step 4: Installing ROS 2 (Foxy)

1. **Setting Up the Sources List:**
   - I opened a terminal and entered:
     ```bash
     sudo apt update && sudo apt install curl -y
     sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
     sudo sh -c 'echo "deb [arch=amd64] http://packages.ros.org/ros2/ubuntu $(lsb_release -cs) main" > /etc/apt/sources.list.d/ros2-latest.list'
     ```

2. **Installing ROS 2 Foxy:**
   - I updated the package list:
     ```bash
     sudo apt update
     ```
   - I installed ROS 2 Foxy:
     ```bash
     sudo apt install ros-foxy-desktop
     ```

3. **Setting Up the Environment:**
   - I added the following line to my `.bashrc`:
     ```bash
     echo "source /opt/ros/foxy/setup.bash" >> ~/.bashrc
     source ~/.bashrc
     ```

4. **Installing Dependencies for Building Packages:**
   - I installed the following:
     ```bash
     sudo apt install python3-colcon-common-extensions
     ```

5. **Trying Some Examples:**
   - I sourced the ROS 2 setup script:
     ```bash
     source /opt/ros/foxy/setup.bash
     ```
   - I ran a demo:
     ```bash
     ros2 run demo_nodes_cpp talker
     ```

By following these steps, I successfully installed VirtualBox, set up Ubuntu 20.04 within a virtual machine, and installed both ROS 1 (Noetic) and ROS 2 (Foxy) on my system.
