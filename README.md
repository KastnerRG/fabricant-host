# fabricant-host
fabricant.ucsd.edu configuration

# Bootstrapping
1. Create a `fabricant-admin` user and add it to the sudoers group
1. Create and install a GitHub deploy key
`. Ensure that the system can SSH into itself
1. Install `sudo`, `git`, `python3.11-venv`
1. Clone this repo
```
git clone git@github.com:KastnerRG/fabricant.git /home/fabricant-admin/fabricant-host
```
1. Install Bitwarden Client
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash # install nvm
source ~/.bashrc # activate nvm
nvm install v24.3.0 # install node 24.3.0
nvm exec v24.3.0 # activate node
npm install -g @bitwarden/cli # installs bw
bw config server https://vault.e4e-gateway.ucsd.edu # configures bw to our vault
bw login # Logs in
```
1. Bootstrap creds
```
bw unlock --raw > ~/fabricant-host/.bw_session
```
1. Create a venv at `~/fabricant-host/.venv`
```
python3 -m venv ~/fabricant-host/.venv`
```
1. Activate venv
```
source ~/fabricant-host/.venv/bin/activate
```
1. Install dependencies
```
python -m pip install --upgrade pip poetry
cd ~/fabricant-host/
poetry install
```