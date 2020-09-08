# VirtualBox Server Ansible

Because of the COVID-19 pandemic, the fall 2020 semester is remote for all my classes at university. In many classes, we need VirtualBox to setup VMs on our local computers. This causes a few problems since most of our lab assignments are in teams. We cannot really have a good collaboration environment with screen sharing tools. Only a user can do the manipulations, and one teammate must host the VM on his computer. Therefore, the host must always be present to work on the assignment.

This Ansible Playbook attempt at fixing this by allowing a team to create a machine quickly with VirtualBox and set up a VNC service where they can connect. The machine can be hosted anywhere.

In my case, it is a DigitalOcean droplet with dedicated CPU cores to limit the overhead of virtualization. The playbook allows the droplet to be deleted when not used to save money and to create it on a need basis. The data can be persisted if another disk is attached to the droplet. With this setup, you are only billed for the storage and a few hours of computing instead of the entire duration of the semester.

These Ansible configuration scripts are used to set up a Ubuntu 20.04LTS machine with VirtualBox, VNC, and an LXDE desktop environment.

## Usage
1. Copy the file `hosts.example` to `hosts` and replace `vboxserver-host` with the IP address of the machine.
2. Run the command on your local machine to set up the machine 
```
ansible-playbook -i hosts site.yml
```
3. Connect to the machine using ssh and make sure to forward the VNC port to your machine.
```
ssh -L 5901:localhost:5901 root@host.example
```
4. Connect to the VNC server with this information

| Information | Value      |
| ----------- |:-----------|
| hostname    | localhost  |
| port        | 5901       |
| password    | 123456     |