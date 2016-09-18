```bash
adduser jimihendrix
usermod -aG sudo jimihendrix

ssh-keygen
ssh-copy-id jimihendrix@SERVER_IP_ADDRESS

sudo nano /etc/ssh/sshd_config
  # PasswordAuthentication no
  # PubkeyAuthentication yes
  # ChallengeResponseAuthentication no

sudo systemctl reload sshd

# Test Log In
ssh jimihendrix@SERVER_IP_ADDRESS

sudo ufw app list
sudo ufw allow OpenSSH
sudo ufw enable
sudo ufw status
```
