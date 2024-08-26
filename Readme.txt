

Running the Shell Script for User Creation, Network Configuration, and Firewall Management
Overview
This script automates the process of:

Creating a new user and adding it to a specified group.
Configuring network settings (IP address, netmask, gateway, and DNS).
Disabling the firewall.
Important: Use this script with caution, especially when disabling the firewall, as it can expose your system to security risks.

Prerequisites
Linux Distribution: This script is tailored for RHEL/CentOS-based systems. For other distributions, you may need to adjust the network configuration commands.
Privileges: Ensure you have sudo privileges to execute administrative commands.
Dependencies: sudo, systemctl, and basic shell utilities.
Script Usage
Download or Create the Script:

Save the following script content to a file, e.g., setup.sh:


#!/bin/bash

# Variables
USERNAME="newuser"
GROUPNAME="newgroup"
IP_ADDRESS="192.168.1.100"
NETMASK="255.255.255.0"
GATEWAY="192.168.1.1"
DNS="8.8.8.8"
INTERFACE="eth0" # Change this to your network interface name

# Create a new user
echo "Creating user $USERNAME..."
sudo useradd -m $USERNAME

# Set a password for the new user
echo "Setting password for $USERNAME..."
echo "$USERNAME:password" | sudo chpasswd

# Create a new group
echo "Creating group $GROUPNAME..."
sudo groupadd $GROUPNAME

# Add the user to the group
echo "Adding user $USERNAME to group $GROUPNAME..."
sudo usermod -aG $GROUPNAME $USERNAME

# Assign IP address and configure network
echo "Configuring network settings for interface $INTERFACE..."
sudo tee /etc/sysconfig/network-scripts/ifcfg-$INTERFACE <<EOF
DEVICE=$INTERFACE
BOOTPROTO=static
IPADDR=$IP_ADDRESS
NETMASK=$NETMASK
GATEWAY=$GATEWAY
DNS1=$DNS
ONBOOT=yes
EOF

# Restart network service to apply changes
echo "Restarting network service..."
sudo systemctl restart network

# Disable the firewall (Warning: This can expose your system to security risks)
echo "Disabling the firewall..."
sudo systemctl stop firewalld
sudo systemctl disable firewalld

echo "Setup complete."
Make the Script Executable:

Open a terminal and navigate to the directory containing setup.sh. Run the following command to make it executable:

chmod +x setup.sh
Run the Script:

Execute the script with sudo to ensure it has the necessary permissions:

sudo ./setup.sh
Verify the Changes:

User Creation: Check if the user and group have been created:

id newuser
Network Configuration: Verify the network settings with:

ip addr show eth0
Firewall Status: Check the firewall status with:


sudo systemctl status firewalld

Customization
Username and Group: Modify USERNAME and GROUPNAME variables in the script.
Network Settings: Adjust IP_ADDRESS, NETMASK, GATEWAY, DNS, and INTERFACE as needed.
Warnings

Firewall: Disabling the firewall can make your system vulnerable. Consider configuring the firewall properly instead.
Network Configuration: Ensure the network interface name and IP settings match your environment.
For any issues or questions, refer to your system’s documentation or seek assistance from your system administrator.




