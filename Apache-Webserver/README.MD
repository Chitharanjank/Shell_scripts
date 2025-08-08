
---

# Apache Webserver Configuration Script

This Bash script automates the process of **printing server details** and **installing & configuring the Apache webserver** on Linux systems (supports RHEL/CentOS-based and Ubuntu-based distros).

## Features

* Detects OS type (Linux with `yum` or Ubuntu with `apt`)
* Prints basic system details:

  * Current username
  * Private IP address
  * System uptime
  * Current date & time
* Installs Apache webserver (`httpd`)
* Starts and enables Apache service
* Prompts the user to add custom content to the Apache `index.html` page
* Displays public IP for accessing the webserver

## Prerequisites

* A Linux server with internet access
* `sudo` privileges
* Supported OS:

  * RHEL / CentOS (uses `yum`)
  * Ubuntu / Debian (uses `apt`)

## Usage

1. **Clone the repository**

   ```bash
   git clone https://github.com/Chitharanjank/Shell_scripts.git
   cd Shell-scripts/
   ```

2. **Make the script executable**

   ```bash
   chmod +x apache_setup.sh
   ```

3. **Run the script**

   ```bash
   ./apache_setup.sh
   ```

4. **Follow the prompt**

   * Enter the content you want to display on your web page when prompted.

5. **Access your webserver**

   * The script will print the public IP at the end.
   * Open it in your browser:

     ```
     http://<public-ip>
     ```

## Script Workflow

1. **Check OS Type** → Determines package manager (`yum` or `apt`).
2. **Print System Details** → Shows username, IP, uptime, and date.
3. **Install Apache** → Installs and configures `httpd` server.
4. **Enable Webserver** → Starts and enables Apache on boot.
5. **Create Webpage** → Adds custom content to `/var/www/html/index.html`.
6. **Display Access Info** → Prints public IP to access the site.


## Example Output

```
=====================================
 Checking OS Type
=====================================
OS Type is Linux
=====================================
 System Details are
=====================================
Username: ec2-user
Private IP: 172.31.0.10
uptime:  12:04:32 up 1 day,  3:44,  1 user,  load average: 0.00, 0.00, 0.00
date: Mon Aug 08 12:04:32 UTC 2025
Printing System Details is Done
=====================================
 Configuring Apache webserver
=====================================
Configuring Apache Webserver is Done
=====================================
 Installing and Configuring Apache webserver is Completed
=====================================
You can access it through http://3.110.45.200
```

---

