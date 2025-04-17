# 🖥️ TASK 7: Monitor System Resources Using Netdata

## 🎯 Objective:
Set up real-time system monitoring on an EC2 instance using **Netdata**, a lightweight and powerful monitoring tool.

## 🛠️ Tools Used:
- Netdata (Dockerized)
- AWS EC2 (Ubuntu)
- Docker

## 🔧 How It Was Done:
1. **Launched EC2 Instance** and installed Docker.
2. **Opened Port 19999** in the EC2 security group to allow web access to Netdata dashboard.
3. **Ran Netdata using Docker:**

   ```bash
   sudo docker run -d --name=netdata -p 19999:19999 --cap-add=SYS_PTRACE \
     -v netdataconfig:/etc/netdata \
     -v netdatalib:/var/lib/netdata \
     -v netdatacache:/var/cache/netdata \
     -v /etc/passwd:/host/etc/passwd:ro \
     -v /etc/group:/host/etc/group:ro \
     -v /proc:/host/proc:ro \
     -v /sys:/host/sys:ro \
     -v /etc/os-release:/host/etc/os-release:ro \
     netdata/netdata
