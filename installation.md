# OpenStack installation on ubuntu 22:04

```
sudo apt install git python3-dev libffi-dev gcc libssl-dev
sudo pip3 install -U pip
```

```
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt install -y python3.10 python3.10-venv python3.10-dev
sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.10 1
```

```
sudo apt-get remove python3-pip
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
python3 get-pip.py
```

```
echo 'export PATH=$HOME/.local/bin:$PATH' >> ~/.bashrc
source ~/.bashrc
```

```
git clone https://github.com/ansible/ansible.git
cd ansible
git checkout stable-2.16
pip install .
```


```
pip install git+https://opendev.org/openstack/kolla-ansible@master
```

```
sudo mkdir -p /etc/kolla
sudo chown $USER:$USER /etc/kolla
```

```
sudo mkdir -p /opt/kolla/
cd /opt/kolla/ && sudo git clone https://github.com/openstack/kolla-ansible.git
```

```
cp -r /opt/kolla/kolla-ansible/etc/kolla/* /etc/kolla/
cp -r /opt/kolla/kolla-ansible/ansible/inventory/* /etc/kolla/
```


```
kolla-ansible install-deps
```



## Kolla passwords
##### Passwords used in our deployment are stored in /etc/kolla/passwords.yml file. All passwords are blank in this file and have to be filled either manually or by running random password generator:
```
kolla-genpwd
```


## in /etc/ansible/ansible.cfg

```
host_key_checking=False
pipelining=True
forks=100
```
```
 pip install --user cffi
```

```
ansible-galaxy collection install community.general
ansible-galaxy collection install ansible.posix
ansible-galaxy collection install ansible.netcommon
```

```
sudo cp -r ~/.ansible/collections/ansible_collections/community/general /opt/kolla/kolla-ansible/ansible/roles/
```


```
kolla-ansible prechecks -i multinode
```

```
kolla-ansible deploy -i <path/to/multinode/inventory/file>
```

