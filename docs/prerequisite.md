This guide provides step by step instructions to deploy hujan io

## System Requirements
The system machine must satisfy the following requirements :  
- 1 network interface  
- 4 Core of CPU  
- 4 GiB of RAM  
- 50 GiB of disk space  
- Python 3.6.1 installed  
- Kolla Ansible v9.3.1 installed  
- MAAS v2.8.2 installed  


**Hujan** using MAAS (Metal as a Service) to manage barematal, and Kolla-ansible as the basis of deployment tools.

## Install Kolla ansible

### Install Dependencies
- Update the package index.  
```
sudo apt update
```

- Install python build dependencies.  
```
sudo apt install python3-dev libffi-dev gcc libssl-dev
```

- Install pip.  

```
sudo apt install python3-pip
```

- Ensure the latest version of pip installed.  
```
sudo pip3 install -U pip
```

- Install Ansible. Kolla ansible requires at least Ansible 2.9 and support up to ansible 2.9.  
```
sudo apt install ansible
```

If the installed ansible version not meet requirement you can use pip. 

```
sudo pip3 install -U 'ansible<2.10'
```

- Install Kolla Ansible.  
```
sudo pip3 install kolla-ansible==9.3.1
```

- Create the `/etc/kolla` directory.
```
sudo mkdir -p /etc/kolla
sudo chown $USER:$USER /etc/kolla
```

- Copy `globals.yaml` and `password.yaml` to `/etc/kolla/`.  
```
cp -r /usr/local/share/kolla-ansible/etc_examples/kolla/* /etc/kolla
```

- Create `kolla` user
```
sudo useradd kolla
```