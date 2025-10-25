# How Tos Raspi-5
https://github.com/gimlin0610/k3s-ansible/blob/raspi5-hase10/raspi5_debian_13_howto.md
## Set predictable nic names
sudo raspi-config
-> advanced configuration
## Boot cmd 
vi /boot/firmware/cmdline.txt
add to end of line 
cgroup_memory=1 cgroup_enable=memory

## Example for fix IP
sudo nmcli con mod "Wired connection 1" ipv4.addresses "192.168.179.92/24, 192.168.181.92/24"  ipv4.method manual
sudo nmcli con mod "Wired connection 1" ipv4.gateway 192.168.179.1
sudo nmcli con mod "Wired connection 1" ipv4.dns 192.168.179.1
sudo nmcli con down "Wired connection 1" && sudo nmcli con up "Wired connection 1"

sudo nmcli con mod "Wired connection 1" ipv4.addresses 192.168.179.91/24 ipv4.method manual
sudo nmcli con mod "Wired connection 1" ipv4.addresses 192.168.179.92/24 ipv4.method manual

sudo nmcli con mod "Wired connection 1" ipv4.addresses 192.168.179.93/24 ipv4.method manual
sudo nmcli con mod "Wired connection 1" ipv4.gateway 192.168.179.1
sudo nmcli con mod "Wired connection 1" ipv4.dns 192.168.179.1
sudo nmcli con down "Wired connection 1" && sudo nmcli con up "Wired connection 1"

## swap off

root@rabbit93:~# sudo swapoff -a
root@rabbit93:~# swapon --show
root@rabbit93:~# sudo systemctl mask swap.target
Created symlink '/etc/systemd/system/swap.target' → '/dev/null'.
root@rabbit93:~# reboot
