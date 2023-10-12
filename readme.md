# Prerequisites

I was using ansible to set up my Raspberry Pi due to numerous situations when my Raspberry PI got either messed up to a point when it is easier to just reinstall everything from scratch. Doing these reinstalls and re-setups each time by hand is pure torture so to trim the hassle I've used ansible there are just few commands you need get through assuming a clean install of Raspberry Pi OS (32 bit, Bookworm):

## On your Raspberry PI(s):
1.  Just enable the I2C via `sudo raspi-config` => `Interface Options` => `I2C` => `Yes`

2. It would depend on the type of camera you use (in my case ov9281) you would need to edit your `/boot/config.txt` and place `dtoverlay=ov9281` into an end of the file

3. Install Ansible to your Raspberry Pi(s) `sudo apt install ansible`

4. Reboot

## On your ansible control node (Any machine from which you will be controlling your fleet):
1. Make sure you are able to SSH into your Raspberry Pi(s) without password (One way to do it is to use `ssh-copy-id your_login@192.168.0.XXX` or `ssh-copy-id your_login@your_pi_hostname` to copy your public SSH key to your Raspberry Pi's authorized_keys)

2. Run `ansible-playbook -i ansible.hosts.ini ansible.init.yml` which would initialize your Raspberry PI(s) (just make sure that `ansible.hosts.ini` and `ansible.init.yml` are present in your current directory from which you are running the above command and that ansible.hosts.ini contains IP addresses or DNS names of your target Raspberry PIs)
