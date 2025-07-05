# fabricant-host
fabricant.ucsd.edu configuration

# Bootstrapping
1. Create a `fabricant-admin` user and add it to the sudoers group
1. Create and install a GitHub deploy key
`. Ensure that the system can SSH into itself
1. Install `sudo`, `git`, `python3.11-venv`
1. Create a venv at `~/fabricant/.venv`
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