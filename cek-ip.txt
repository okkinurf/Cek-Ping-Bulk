#!/bin/bash

# Define color codes
GREEN='\033[0;32m'
RED='\033[0;31m'
NC='\033[0m' # No Color

# Function to check IP status
check_ip() {
    local ip=$1
    local timestamp=$(date "+%Y-%m-%d %H:%M:%S")  # Capture current date and time
    # Ping the IP with fewer packets to reduce time
    if ping -c 1 -W 1 "$ip" > /dev/null 2>&1; then
        printf "%-20s: ${GREEN}%-10s${NC}  [%s]\n" "$ip" "UP !!" "$timestamp"
    else
        printf "%-20s: ${RED}%-10s${NC}  [%s]\n" "$ip" "DOWN" "$timestamp"
    fi
}

# Read IPs from the list-ip.txt file, strip /23, and check each IP in parallel
while IFS= read -r ip; do
    clean_ip=$(echo "$ip" | awk -F'/' '{print $1}')
    check_ip "$clean_ip" &
done < list-ip.txt

# Wait for all background jobs to complete
wait
