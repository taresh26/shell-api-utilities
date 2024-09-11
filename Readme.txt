# Multiple VMware VM Deployment Script

## Overview

This PowerShell script automates the deployment of multiple virtual machines (VMs) in a VMware vSphere environment using PowerCLI. It allows the user to specify the number of VMs to be created, and it will automatically clone a VM template and configure each VM accordingly.

The script is designed for system administrators and developers who need to quickly scale up virtual environments by deploying large numbers of VMs.

## Features

- Deploy multiple VMs with a single script
- Clone VMs from a pre-defined template
- Automatic configuration of datastore, network, and resource pool
- Start VMs automatically after deployment

## Prerequisites

1. **PowerCLI**: This script requires VMware PowerCLI. You can install it by running the following command:

   ```powershell
   Install-Module -Name VMware.PowerCLI -Force
