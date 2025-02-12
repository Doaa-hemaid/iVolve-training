# Ping Sweep Script

## Description
This script pings every server in the `192.168.225.x` subnet (where `x` ranges from 0 to 255).  
- If the ping succeeds, it displays: `Server 192.168.225.x is up and running`.  
- If the ping fails, it displays: `Server 192.168.225.x is unreachable`.

## Script: `ping_sweep.sh`
```bash
#!/bin/bash
# Loop through the range 0-255
for x in {0..255}; do
  # Ping the server with a single packet and 1-second timeout
  if ping -c 1 -W 1 192.168.225.$x &> /dev/null; then
    echo "Server 192.168.225.$x is up and running"
  else
    echo "Server 192.168.225.$x is unreachable"
  fi
done
```

## How to Run
1. Save the script as `ping_sweep.sh`.
2. Make it executable:
   ```bash
   chmod +x ping_sweep.sh
   ```
3. Run the script:
   ```bash
   ./ping_sweep.sh
   ```
