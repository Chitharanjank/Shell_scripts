#!/bin/bash

### This script will print server details & Configure Apache webserver

Header() {
    echo "====================================="
    echo " $1 "
    echo "====================================="
}

Check_os_type() {
    Header "Checking OS Type"
    OS=$(grep -w NAME /etc/os-release | awk -F= '{print $2}' | tr -d '"')
    
    if [[ "$OS" == "Ubuntu" ]]; then
        echo "OS Type is Ubuntu"
        pkg_manager="apt"
        apache_pkg="apache2"
    elif [[ "$OS" == "CentOS Linux" || "$OS" == "Red Hat Enterprise Linux" || "$OS" == "Amazon Linux" ]]; then
        echo "OS Type is RHEL/CentOS/Amazon Linux"
        pkg_manager="yum"
        apache_pkg="httpd"
    else
        echo "Unsupported OS: $OS"
        exit 1
    fi
}

check_status() {
    if [ $? -ne 0 ]; then
        echo "There was an error while $1"
        exit 1
    else
        echo "$1 is Done"
    fi
}

system_detail() {
    Header "System Details"
    echo "Username: $(whoami)"
    echo "Private IP: $(hostname -I | awk '{print $1}')"
    echo "Uptime: $(uptime -p)"
    echo "Date: $(date)"
    check_status "Printing System Details"
}

configure_Apache() {
    Header "Configuring Apache Webserver"
    
    # Update package list if using apt
    if [[ "$pkg_manager" == "apt" ]]; then
        sudo apt update -y
    fi
    
    sudo $pkg_manager install $apache_pkg -y
    check_status "Installing Apache"
    
    sudo systemctl start $apache_pkg
    check_status "Starting Apache"
    
    sudo systemctl enable $apache_pkg
    check_status "Enabling Apache on boot"
    
    read -p "Enter content to add in index.html file: " Content
    echo "$Content" | sudo tee /var/www/html/index.html > /dev/null
    check_status "Creating index.html with your content"
}

testing() {
    Header "Apache Webserver Setup Completed"
    echo "You can access it through: http://$(curl -s ifconfig.me)"
}

# Script Execution Flow
Check_os_type
system_detail
configure_Apache
testing