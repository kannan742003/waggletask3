# EC2 Instance Setup with Username/Password Authentication

This repository contains documentation outlining the steps taken to spin up an EC2 instance in AWS and enable username/password authentication for SSH login.

## Steps

### 1. Spin up an EC2 Instance

1. **Login to AWS Console**: Access the AWS Management Console with your credentials.
2. **Navigate to EC2 Dashboard**: Select "EC2" from the services dropdown menu.
3. **Launch Instance**: Click on "Launch Instance" to initiate the instance creation process.
4. **Choose AMI**: Select the desired Amazon Machine Image (AMI) like CentOS or Ubuntu.
5. **Choose Instance Type**: Opt for the "t2.micro" instance type, suitable for your requirements.
6. **Configure Instance**: Set up instance details such as VPC, subnet, and other configurations as needed.
7. **Add Storage**: Configure storage settings including size and type.
8. **Add Tags (Optional)**: Add any tags for identification or organization purposes.
9. **Configure Security Group**: Create or select a security group with necessary inbound and outbound rules, including SSH access (port 22).
10. **Review and Launch**: Review instance details and configurations, then click "Launch".
11. **Key Pair (Optional)**: Choose to create a new key pair or use an existing one for SSH access to the instance.
12. **Launch Instance**: Confirm launch, and the instance will be provisioned according to the selected configurations.

### 2. Enable Password Authentication for SSH

1. **Connect to the EC2 Instance**: Use an SSH client or terminal to connect to the instance using the private key.
   ```bash
   ssh -i /path/to/private-key.pem ubuntu@your-instance-public-ip

2.Modify SSH Configuration: Edit the SSH server configuration file to enable password authentication.

  sudo nano /etc/ssh/sshd_config

  Change PasswordAuthentication no to PasswordAuthentication yes.

3.Restart SSH Service: Restart the SSH service to apply the changes.

  sudo systemctl restart sshd

4.Set Password for User: Set a password for the user you want to log in with.

  sudo passwd ubuntu

5.Test Connection: Ensure you can now log in using SSH with the username and password.

  ssh ubuntu@your-instance-public-ip
