```bash
# Setup the user
adduser jimihendrix
usermod -aG sudo jimihendrix

# Create (local) SSH keys and copy the public key to the server
ssh-keygen
ssh-copy-id jimihendrix@SERVER_IP_ADDRESS

# Disable password login over SSH
sudo vim /etc/ssh/sshd_config
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

sudo apt-get update
sudo apt-get install zsh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
sudo apt-get install apache2
sudo ufw allow in "Apache Full"
sudo vim /etc/apache2/apache2.conf
  # add a new <Directory> listing for sites directory
  # <Directory /home/jimihendrix/sites>
  #         Options Indexes FollowSymLinks
  #         AllowOverride None
  #         Require all granted
  # </Directory>
  
sudo apt-get install python-letsencrypt-apache
sudo letsencrypt --apache # Run this later to renew certificates also

gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
\curl -sSL https://get.rvm.io | bash -s stable
rvm install 2.3.1
rvm --default use 2.3.1
echo "gem: --no-ri --no-rdoc" >> ~/.gemrc
gem install bundler
gem install passenger

sudo apt-get install libcurl4-openssl-dev
sudo apt-get install apache2-dev
passenger-install-apache2-module

sudo apt-get install libapache2-mod-passenger

```
