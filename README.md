# addfire Bash Script

## Description

This Bash script is designed to simplify the process of adding a specified port to the firewall using `firewall-cmd`. It performs the following actions:

1. Adds the specified port to the firewall.
2. Reloads the firewall rules.
3. Displays the list of ports.

## Usage

To use the script, provide the desired port as a command-line argument:

```bash
./addfire <port>
```

Example:

```bash
./addfire 65300
```

## Installation

1. Save the script to a file, e.g., `addfire`.

```bash
#!/bin/bash

# Check if port argument is provided
if [ -z "$1" ]; then
    echo "Usage: $0 <port>"
    exit 1
fi

# Get the port from the command line argument
port="$1"

# Add the port to the firewall
sudo firewall-cmd --add-port="${port}/tcp" --permanent

# Reload the firewall
sudo firewall-cmd --reload

# Display the list of ports
sudo firewall-cmd --list-ports

echo "Port ${port} added to the firewall."
```

2. Make the script executable:

   ```bash
   chmod +x addfire
   ```

3. Move the script to `/usr/local/bin` to make it accessible from anywhere:

   ```bash
   sudo mv addfire /usr/local/bin/
   ```

Now, you can run the script from any location by simply typing `addfire <port>`.

**Note:** Ensure that `/usr/local/bin` is in your system's `PATH`.

## Requirements

- This script assumes the usage of `firewall-cmd` for managing firewall rules.

Feel free to modify the script or adapt it based on your specific firewall configuration or requirements.

