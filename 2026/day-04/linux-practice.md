PROCESS COMMANDS : (ps , top)
SERVICE COMMANDS : (systemctl status , sudo systemctl start ssh)
LOG COMMANDS : (journalctl -u ssh ,  journalctl -n 20)


(Service inspected: SSH)
Command:
systemctl status ssh

Action:
sudo systemctl start ssh

Verification:
systemctl is-active ssh

Expected output:
active
