## DevOpsFetch ----- Devops_HNG_stage5 Task
DevOpsfetch is a useful command-line tool designed for DevOps professionals to quickly retrieve and display critical system information. It provides quick, easy access to details about active ports, Docker containers, Nginx configurations, user logins, and system activities within specified time ranges.

### Features
- Display active ports and services
- List Docker images and containers
- Show Nginx domain configurations
- View user login information
- Monitor system activities within custom time ranges
- Formatted output for easy readability

### Installation
- Clone this repository:
- Make the installation script executable:

```bash
chmod +x install_script.sh
```
Run the installation script as root:

```bash
sudo ./install_script.sh
```

Run to view help options
```bash
devopsfetch -h
```

Usage Options: 
    -p, --port [PORT]: Display active ports or specific port info 
    -d, --docker [NAME]: List Docker images/containers or specific container info 
    -n, --nginx [DOMAIN]: Display Nginx domains or specific domain config 
    -u, --users [USER]: List users and last login or specific user info 
    -t, --time RANGE: Display activities within a time range (e.g., '1 hour ago') 
    -h, --help: Display help message

Examples

1. Display all active ports:

```bash
devopsfetch -p
```

2. Display information about a specific port:

```bash
devopsfetch -p 80
```

3. List all Docker containers:

```bash
devopsfetch -d

```

4. Get detailed information about a specific Docker container:

```bash
devopsfetch -d container_name

```

5. Display all Nginx domains:

```bash
devopsfetch -n

```

6. Get Nginx configuration for a specific domain:

```bash
devopsfetch -n example.com

```

7. List all users and their last login times:

```bash
devopsfetch -u

```

8. Get last login information for a specific user:

```bash
devopsfetch -u username

```

9. Display activities within the last hour:

```bash
devopsfetch -t '1 hour ago'

```

DevOpsFetch supports shows system activities within specific date ranges:

### To show activities for a specific date:

```bash
devopsfetch --time start-date (end-date) 
```

Installation Detailed Process
The `install_script.sh` script performs the following actions:

1. Updates the system package list.
2. Installs necessary dependencies:
    - nginx
    - docker.io
    - jq (for JSON parsing)
3. Copies the main `devopsfetch` script to `/usr/local/bin/`, making it accessible system-wide.

4. Sets the appropriate permissions to make the script executable.

5. Creates a systemd service file (`/etc/systemd/system/devopsfetch.service`) to run the script periodically.

6. Enables and starts the systemd service.

7. Sets up log rotation for the devopsfetch logs to manage log file sizes and retention.

After running the installation script, devopsfetch will be installed as a system-wide command and a background service will be set up to periodically collect and log system information.

Note: The installation requires root privileges to install packages and set up system services.

### To uninstall devopsfetch:

- Stop and disable the systemd service:
```bash
    sudo systemctl stop devopsfetch.service
    sudo systemctl disable devopsfetch.service
```

- Remove the service file:
```bash
    sudo rm /etc/systemd/system/devopsfetch.service
```

- To Remove Main script:
```bash
    sudo rm /usr/local/bin/devopsfetch
```

- Remove the log rotation configuration
```bash
    sudo rm /etc/logrotate.d/devopsfetch
```