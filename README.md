# setting-up-wsl-ansible-to-control-windows-host

### Below command on Windows 10 box where the WSL is Installed

```powershell
# Configure Remoting for Ansible 
iex ((New-Object System.Net.WebClient).DownloadString('https://raw.githubusercontent.com/ansible/ansible/devel/examples/scripts/ConfigureRemotingForAnsible.ps1'))
# Enable WsMan
Enable-WSManCredSSP -Role Server -Force
```
### Below command on WSL (Tested on ubuntu)

```bash
# Install Python and Python pip so ansible can be installed later.
# Go to userhome folder
cd ~
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
kinit <YOUR_USERNAME>
# Verify if the Kerberos all set
echo "Verifying if the kerberos is all"
klist

# Lets Test if the windows machine can be pinged from Windows Subsystem Linux
ansible windows -i hosts -m win_ping

# Gather all facts about your windows machine
ansible windows -i hosts -m setup


```
