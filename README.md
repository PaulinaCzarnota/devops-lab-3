This repository contains my Lab 3 - Vagrant solution for the Introduction to DevOps module in the third year of the Computer Science course at TU Dublin.

# Overview

The objective of this lab is to automate the deployment of a Flask web application using Vagrant. The lab sets up a Debian VM, installs necessary dependencies, provisions a Flask app, and enables port forwarding for external access.

# Key Features

### **Automated VM Setup**
- Vagrantfile automates the provisioning of a Debian-based virtual machine.
- Uses VirtualBox as the VM provider.
- Port forwarding (5000 → 1234) for external access.

### **Flask Web Application**
- A simple Flask app serving two routes:
  - "/" → Displays "Hello, World!" with a link to `/about`.
  - "/about" → Displays "This is a Flask web app running in a Linux VM."

### **Provisioning Steps**
- **Dependency Installation:** Installs Python, Flask, Git, and other required packages.
- **Virtual Environment Setup:** Creates and activates a Python virtual environment.
- **App Deployment:** Uploads and runs the Flask app automatically on VM startup.
