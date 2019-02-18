# setting-up-wsl-ansible-to-control-windows-host

### Below command on WSL (Tested on ubuntu)

```bash
# Install Python and Python pip so ansible can be installed later.
# Go to userhome folder
#cd ~
sudo apt-get install python -y
sudo apt-get install python-pip -y
sudo pip install virtualenv
virtualenev ansibleenv
source ansibleenv/bin/activate
pip install ansible
ansible --version
ansible localhost -m ping
pip install "pywinrm>=0.3.0"
sudo apt-get install libkrb5-dev
pip install pywinrm[kerberos]

pip install pywinrm[credssp]
sudo apt-get install krb5-user
# Below Command will ask for the Password
kinit vpandey
# Verify if the Kerberos all set
echo "Verifying if the kerberos is all"
klist
# Lets Test if the windows machine can be pinged from Windows Subsystem Linux
ansible windows -i hosts -m win_ping
```
