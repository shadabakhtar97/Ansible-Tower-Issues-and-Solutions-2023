# Ansible-Tower-Issues-and-Solutions-2023
Ansible Tower Issues and Solutions
### Issue
SSH password: 
PLAY [New user is created] *****************************************************
TASK [Gathering Facts] *********************************************************
fatal: [web01.example.com]: UNREACHABLE! => {"changed": false, "msg": "Failed to connect to the host via ssh: ssh: connect to host web01.example.com port 22: Connection timed out", "unreachable": true}
fatal: [web02.example.com]: UNREACHABLE! => {"changed": false, "msg": "Failed to connect to the host via ssh: ssh: connect to host web02.example.com port 22: Connection timed out", "unreachable": true}
PLAY RECAP *********************************************************************
web01.example.com          : ok=0    changed=0    unreachable=1    failed=0    skipped=0    rescued=0    ignored=0   
web02.example.com          : ok=0    changed=0    unreachable=1    failed=0    skipped=0    rescued=0    ignored=0

### Solution

vim /etc/ssh/ssh_config

![image](https://github.com/shadabakhtar97/Ansible-Tower-Issues-and-Solutions-2023/assets/43212251/0193405b-bc03-4c7a-afd8-b37545d57cb5)


The error message indicates that Ansible is unable to connect to the hosts "web01.example.com" and "web02.example.com" via SSH. The most common reasons for this error include:

1. **SSH Service not running**: Ensure that the SSH service is running on the target hosts. Check if the SSH daemon is running and configured to listen on port 22.

2. **Firewall**: Check if there is a firewall on the target hosts blocking incoming connections on port 22. If so, you may need to adjust the firewall settings to allow SSH connections.

3. **Network Connectivity**: Ensure that there is network connectivity between the machine running Ansible and the target hosts. The "Connection timed out" error suggests that the Ansible host cannot reach the target hosts.

4. **SSH Key Authentication**: If you are using SSH key authentication, ensure that the public key is present in the `authorized_keys` file on the target hosts for the specified user.

5. **Host Resolution**: Make sure that the hostnames "web01.example.com" and "web02.example.com" are correctly resolved to IP addresses. You can check this using tools like `ping` or `nslookup`.

6. **User Permissions**: Ensure that the user specified in your Ansible playbook has the necessary permissions to connect via SSH and perform the required tasks on the target hosts.

### ------------------------------------------------------------------------------------------
