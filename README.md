# Note 

## IBus Bamboo - Bộ gõ tiếng Việt cho Linux

```sh
sudo add-apt-repository ppa:bamboo-engine/ibus-bamboo
sudo apt-get update
sudo apt-get install ibus ibus-bamboo --install-recommends
ibus restart
# Đặt ibus-bamboo làm bộ gõ mặc định
env DCONF_PROFILE=ibus dconf write /desktop/ibus/general/preload-engines "['BambooUs', 'Bamboo']" && gsettings set org.gnome.desktop.input-sources sources "[('xkb', 'us'), ('ibus', 'Bamboo')]"
init 6
```
## NOTEPADQQ
```sh
sudo add-apt-repository ppa:notepadqq-team/notepadqq
sudo apt-get update
sudo apt-get install notepadqq
```

## CHROME
```sh
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo apt install ./google-chrome-stable_current_amd64.deb
```


## SSH
- Generate a Public Key from a Private Key Using ssh-keygen

```sh
 ssh-keygen -f <PRIVATE_KEY_FILE>.pem -y
```
- Change SSH port: Edit line 15 
```sh
nano /etc/ssh/sshd_config

```    
- Restart SSH service
```sh
service sshd restart
```

- Create a pem file to login without password and without copy local keys to remote server

1. Login with account user (not root)

```
mkdir pem
cd pem
ssh-keygen -b 2048 -f identity -t rsa
```

2. Copy public key contents to authorized_keys

```
cat identity.pub >> ~/.ssh/authorized_keys
```

3. Disable Password Authentication

```
sudo nano /etc/ssh/sshd_config
```

Change to no to disable tunnelled clear text passwords

PasswordAuthentication no

4. Restart SSH

```
sudo service ssh restart
```

5. Download your private key to client side

```
cat ~/.ssh/pem/identity
```

6. Set permission for pem on your local

```
sudo chmod 600 identity.pem
```

7. Test login

```
ssh -i identity.pem user@vps-ip
```
## VMWARE
- Install
```
sudo apt update
sudo apt install build-essential linux-headers-generic
wget --user-agent="Mozilla/5.0 (X11; Linux x86_64; rv:60.0) Gecko/20100101 Firefox/60.0" https://www.vmware.com/go/getplayer-linux
chmod +x getplayer-linux
sudo ./getplayer-linux --required --eulas-agreed
```
- Fix 
```
wget https://raw.githubusercontent.com/rune1979/ubuntu-vmmon-vmware-bash/master/wm_autoupdate_key.sh
sudo chmod +x wm_autoupdate_key.sh
./wm_autoupdate_key.sh
```

## XAMPP Ubuntu
### Download 
```
sudo -i
sudo apt install net-tools 
mkdir xampp
cd xampp
wget https://zenlayer.dl.sourceforge.net/project/xampp/XAMPP%20Linux/8.0.28/xampp-linux-x64-8.0.28-0-installer.run    
```
### Setup 
```
chmod 755 xampp-linux-x64-8.0.28-0-installer.run
./xampp-linux-x64-8.0.28-0-installer.run
```

- Next and next. Finish Uncheck Launch Xampp.
### Run 
```
sudo /opt/lampp/lampp start
```

