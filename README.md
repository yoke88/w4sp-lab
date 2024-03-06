tested on kali 2022.3 ,thanks the author of https://medium.com/@vaibjav2raj/setting-up-the-w4sp-lab-in-2020-d4df6a3d2a5e

``` bash
# after install kali ,First change to root.

sudo useradd -m w4sp-lab -s /bin/bash -G sudo -U

# Set the password

passwd w4sp-lab

# Log out and change to user w4sp-lab then download or clone the lab from this repo

sudo apt install -y python3-docker

sudo apt install wireshark net-tools ethtool xterm

sudo python3 w4sp_webapp.py

# After all the images are loaded a browser may or may not open automatically. Don’t panic. Open a firefox tab and enter this address.

# http://127.0.0.1:5000
```
![image](https://github.com/yoke88/w4sp-lab/assets/3146226/dcede8a9-961b-4279-bed5-9bd7f262ee22)

![image](https://github.com/yoke88/w4sp-lab/assets/3146226/90001664-c7e9-424a-ab5a-92767c581782)
