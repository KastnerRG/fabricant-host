# fabricant-host
fabricant.ucsd.edu configuration

# Bootstrapping
1. Create a `fabricant-admin` user and add it to the sudoers group
1. Create and install a GitHub deploy key
`. Ensure that the system can SSH into itself
1. Install `sudo`, `git`, `python3.13-venv`
1. Clone this repo
```shell
git clone git@github.com:KastnerRG/fabricant-host.git /home/fabricant-admin/fabricant-host
```
5. Install Bitwarden Client
```shell
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash # install nvm
source ~/.bashrc # activate nvm
nvm install v24.3.0 # install node 24.3.0
nvm exec v24.3.0 # activate node
npm install -g @bitwarden/cli # installs bw
bw config server https://vault.e4e-gateway.ucsd.edu # configures bw to our vault
bw login # Logs in
```
6. Bootstrap creds
```shell
bw unlock --raw > ~/fabricant-host/.bw_session
```
7. Create a venv at `~/fabricant-host/.venv`
```shell
python3 -m venv ~/fabricant-host/.venv
```
8. Activate venv
```shell
source ~/fabricant-host/.venv/bin/activate
```
9. Install dependencies
```shell
python -m pip install --upgrade pip poetry
cd ~/fabricant-host/
poetry install
```
1. Install GitHub Runner
Instead of running `./run.sh`, execute the following
```shell
sudo ./svc.sh install fabricant-admin
sudo ./svc.sh start
```
1. Navigate to the most recent action and rerun it.
