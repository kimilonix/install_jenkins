# Jenkins Installation on Ubuntu

Ansible Playbook for Installing Jenkins on Ubuntu

This guide provides step-by-step instructions for installing Jenkins on an Ubuntu server. Jenkins is an open-source automation server that helps automate parts of the software development process.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Installation Steps](#installation-steps)
- [Accessing Jenkins](#accessing-jenkins)
- [Post-Installation Setup](#post-installation-setup)
- [Uninstalling Jenkins](#uninstalling-jenkins)
- [Troubleshooting](#troubleshooting)

## Prerequisites

Before you begin, ensure you have:

- An Ubuntu server (20.04 or later recommended).
- A user account with sudo privileges.
- SSH access to the server.

## Installation Steps

1. Update the Package Index:

   Open a terminal and run the following command to update your package index:

   bash
   sudo apt update
   
2. Install Java:

   Jenkins requires Java to run. Install OpenJDK with the following command:

   bash
   sudo apt install openjdk-11-jdk -y
   
   Verify the installation:

   bash
   java -version
   
3. Add the Jenkins Repository:

   Import the GPG key for the Jenkins repository:

   bash
   wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
   
   Then, add the Jenkins repository to your system:

   bash
   sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
   
4. Install Jenkins:

   Update the package index again and install Jenkins:

   bash
   sudo apt update
   sudo apt install jenkins -y
   
5. Start and Enable Jenkins:

   Start the Jenkins service and enable it to start on boot:

   bash
   sudo systemctl start jenkins
   sudo systemctl enable jenkins
   
6. Check Jenkins Status:

   Verify that Jenkins is running with the following command:

   bash
   sudo systemctl status jenkins
   
## Accessing Jenkins

Once Jenkins is installed and running, you can access it through your web browser:

1. Open your web browser.
2. Go to http://your_server_ip:8080.

## Post-Installation Setup

On first access, you will be prompted to unlock Jenkins using an initial admin password.

1. Retrieve the initial admin password with this command:

   bash
   sudo cat /var/lib/jenkins/secrets/initialAdminPassword
   
2. Copy the password and paste it into the setup wizard in your browser.

3. Follow the prompts to complete the setup, including installing suggested plugins and creating an admin user.

## Uninstalling Jenkins

If you need to uninstall Jenkins, use the following command:

bash
sudo apt remove --purge jenkins -y

You may also want to remove any residual configuration files:

bash
sudo rm -rf /var/lib/jenkins /etc/default/jenkins /etc/init.d/jenkins /etc/systemd/system/jenkins.service

## Troubleshooting

- If you encounter issues starting Jenkins, check the logs located at /var/log/jenkins/jenkins.log.
- Ensure that no other services are using port 8080.
- Make sure that Java is correctly installed by verifying java -version.

## Conclusion

You have successfully installed Jenkins on your Ubuntu server! You can now start creating jobs and automating your development processes.

For more information about using Jenkins, visit the [official Jenkins documentation](https://www.jenkins.io/doc/).


▎Notes:

• Customize any sections as needed based on specific requirements or configurations.

• Ensure that any commands are tested before including them in a production environment.
