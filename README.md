# CSLU-UTM-2026

## Install Requirements and Tools

> :warning: **Warning:** Please ensure you have at least 16GB of storage and 4GB of RAM before installing

### Prerequisites:
- Kali Linux or any stable Debian distro
- Minimum 16GB free storage space
- Minimum 4GB RAM


Lab Installation: https://drive.google.com/file/d/1VpxktEHd-Af2bt9xJ-8LIDU3eBeDoALD/view?usp=sharing

Password: (will be revealed in workshop)

---

### Add a new vmnet adapter (pls use **VMware Pro**)

- Edit > Virtual Network Editor
- NAT netowrk adapter

```
172.16.161.0/24
```

Follow like the image below

<img width="1378" height="822" alt="image" src="https://github.com/user-attachments/assets/6ab326c2-0137-4a45-a5e6-5726336e7ecf" />



### Docker

```bash
# Add Docker's official GPG key:
sudo apt update
sudo apt install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
```


```bash
# Add the repository to Apt sources:
sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
Types: deb
URIs: https://download.docker.com/linux/ubuntu
Suites: $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}")
Components: stable
Architectures: $(dpkg --print-architecture)
Signed-By: /etc/apt/keyrings/docker.asc
EOF
```


```bash
sudo apt update

sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

sudo usermod -aG docker $USER
```


---


### BloodHound CLI (CE)

1. Install the tarball

```bash
wget https://github.com/SpecterOps/bloodhound-cli/releases/latest/download/bloodhound-cli-linux-amd64.tar.gz

tar -xvzf bloodhound-cli-linux-amd64.tar.gz

./bloodhound-cli install
```


2. Keep the terminal open until you see the randomly generated password displayed. Save this password for the next step.


```bash
[+] BloodHound is ready to go!
[+] You can log in as `admin` with this password: <Password>
```


3. In a browser, go to `http://localhost:8080/ui/login` and log in with the admin username and the randomly generated password.


4. Reset your password as prompted on first login.


5. Commands below to stop and start BloodHound


```bash
# To stop BloodHound 
./bloodhound-cli containers stop


# To start BloodHound
./bloodhound-cli containers up
```


---


### Impacket

```bash
sudo apt install impacket
```


---


### NetExec

```bash
sudo apt install pipx git
pipx ensurepath
pipx install git+https://github.com/Pennyw0rth/NetExec
```


---


### BloodyAD

```bash
# Create a Python virtual environment if you don't already have one

python3 -m venv bloodyadvenv
source bloodyadvenv/bin/activate

pip install bloodyAD
```

