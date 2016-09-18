```bash
# Setup the user
adduser jimihendrix
usermod -aG sudo jimihendrix

# Create (local) SSH keys and copy the public key to the server
ssh-keygen
ssh-copy-id jimihendrix@SERVER_IP_ADDRESS

# Disable password login over SSH
sudo nano /etc/ssh/sshd_config
  # PasswordAuthentication no
  # PubkeyAuthentication yes
  # ChallengeResponseAuthentication no

sudo systemctl reload sshd

# Test Log In
ssh jimihendrix@SERVER_IP_ADDRESS

# Setup firewall
sudo ufw app list
sudo ufw allow OpenSSH
sudo ufw enable
sudo ufw status
```
