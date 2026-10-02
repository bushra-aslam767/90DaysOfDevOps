# Linux Troubleshooting Runbook

## Target Service
SSH

## Environment Basics

### uname -a
Output:
Linux DESKTOP-NPM00AK 6.18.40.1-microsoft-standard-WSL2 #1 SMP PREEMPT_DYNAMIC Fri Jul 31 22:12:15 UTC 2026 x86_64 GNU/Linux

**Observation:** The command displayed the Linux kernel and system information.

### cat /etc/os-release
Output:
PRETTY_NAME="Ubuntu 26.04.1 LTS"
NAME="Ubuntu"
VERSION_ID="26.04"
VERSION="26.04.1 LTS (Resolute Raccoon)"
VERSION_CODENAME=resolute
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=resolute
LOGO=ubuntu-logo

**Observation:** The system information confirms that the server is running Ubuntu.

## CPU / Memory

### free -h
Output:
           total        used        free      shared  buff/cache   available
Mem:           3.7Gi       478Mi       3.2Gi       4.1Mi       205Mi       3.3Gi
Swap:          1.0Gi          0B       1.0Gi

**Observation:** Memory and swap usage were checked. The available memory was reviewed for resource issues.

## Disk

### df -h
Output:
Filesystem      Size  Used Avail Use% Mounted on
none            1.9G     0  1.9G   0% /usr/lib/modules/6.18.40.1-microsoft-standard-WSL2
none            1.9G  4.0K  1.9G   1% /mnt/wsl
drivers         138G   60G   78G  44% /usr/lib/wsl/drivers
/dev/sdd       1007G  2.0G  954G   1% /
none            1.9G  108K  1.9G   1% /mnt/wslg
none            1.9G     0  1.9G   0% /usr/lib/wsl/lib
rootfs          1.9G  3.3M  1.9G   1% /init
none            1.9G  496K  1.9G   1% /run
none            1.9G     0  1.9G   0% /run/lock
none            1.9G     0  1.9G   0% /run/shm
none            1.9G   80K  1.9G   1% /mnt/wslg/versions.txt
none            1.9G   80K  1.9G   1% /mnt/wslg/doc
C:\             138G   60G   78G  44% /mnt/c
D:\             100G   96M  100G   1% /mnt/d
tmpfs           1.9G     0  1.9G   0% /tmp
none            1.0M     0  1.0M   0% /run/credentials/systemd-journald.service
none            1.0M     0  1.0M   0% /run/credentials/systemd-resolved.service
none            1.0M     0  1.0M   0% /run/credentials/getty@tty1.service
tmpfs           383M   12K  383M   1% /run/user/1000

**Observation:** Disk usage was checked to make sure there is enough available space.

## Network

### ss -tulpn
Output:
Netid   State    Recv-Q   Send-Q      Local Address:Port       Peer Address:Port   Process
udp     UNCONN   0        0              127.0.0.54:53              0.0.0.0:*
udp     UNCONN   0        0           127.0.0.53%lo:53              0.0.0.0:*
udp     UNCONN   0        0          10.255.255.254:53              0.0.0.0:*
udp     UNCONN   0        0               127.0.0.1:323             0.0.0.0:*
udp     UNCONN   0        0               127.0.0.1:323             0.0.0.0:*
udp     UNCONN   0        0                   [::1]:323                [::]:*
udp     UNCONN   0        0                   [::1]:323                [::]:*
tcp     LISTEN   0        4096           127.0.0.54:53              0.0.0.0:*
tcp     LISTEN   0        1000       10.255.255.254:53              0.0.0.0:*
tcp     LISTEN   0        4096        127.0.0.53%lo:53              0.0.0.0:*

**Observation:** Listening ports and network services were checked. SSH can be verified from the listening ports.

## SSH Logs

### journalctl -u ssh -n 50
Output:
-- No entries --

**Observation:** The latest SSH logs were reviewed for errors or warnings.
