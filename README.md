## DevOpsFetch ----- Devops_HNG_stage5 Task
DevOpsfetch is a useful command-line tool designed for DevOps professionals to quickly retrieve and display critical system information. It provides quick, easy access to details about active ports, Docker containers, Nginx configurations, user logins, and system activities within specified time ranges.

Features
Display active ports and services
List Docker images and containers
Show Nginx domain configurations
View user login information
Monitor system activities within custom time ranges
Formatted output for easy readability

### Installation
Clone this repository:

Make the installation script executable:
chmod +x install_script.sh

Run the installation script as root:
sudo ./install_script.sh

Run to view help options
devopsfetch -h
Usage Options: -p, --port [PORT]: Display active ports or specific port info -d, --docker [NAME]: List Docker images/containers or specific container info -n, --nginx [DOMAIN]: Display Nginx domains or specific domain config -u, --users [USER]: List users and last login or specific user info -t, --time RANGE: Display activities within a time range (e.g., '1 hour ago') -h, --help: Display help message

Examples

Display all active ports:
devopsfetch -p
Display information about a specific port:
devopsfetch -p 80
List all Docker containers:
devopsfetch -d
Get detailed information about a specific Docker container:
devopsfetch -d container_name
Display all Nginx domains:
devopsfetch -n
Get Nginx configuration for a specific domain:
devopsfetch -n example.com
List all users and their last login times:
devopsfetch -u
Get last login information for a specific user:
devopsfetch -u username
Display activities within the last hour:
devopsfetch -t '1 hour ago'
DevOpsFetch supports shows system activities within specific date ranges:

### To show activities for a specific date:

devopsfetch --time start-date (end-date) 

Installation Detailed Process
The install_script.sh script performs the following actions:

Updates the system package list.

Installs necessary dependencies:
nginx
docker.io
jq (for JSON parsing)
Copies the main devopsfetch script to /usr/local/bin/, making it accessible system-wide.

Sets the appropriate permissions to make the script executable.

Creates a systemd service file (/etc/systemd/system/devopsfetch.service) to run the script periodically.

Enables and starts the systemd service.

Sets up log rotation for the devopsfetch logs to manage log file sizes and retention.

After running the installation script, devopsfetch will be installed as a system-wide command and a background service will be set up to periodically collect and log system information.

Note: The installation requires root privileges to install packages and set up system services.

### To uninstall devopsfetch:

Stop and disable the systemd service:
sudo systemctl stop devopsfetch.service
sudo systemctl disable devopsfetch.service

Remove the service file:
sudo rm /etc/systemd/system/devopsfetch.service

To Remove Main script:
sudo rm /usr/local/bin/devopsfetch
Remove the log rotation configuration
sudo rm /etc/logrotate.d/devopsfetch