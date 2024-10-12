```
# These initial groups are the only groups required to be modified. The
# additional groups are for more control of the environment.
[control]
# These hostname must be resolvable from your deployment host
controller01 ansible_ssh_user=username ansible_become=True ansible_private_key_file=/homa/username/.ssh/id_rsa ansible_become_password=yourpassword

# The above can also be specified as follows:
#control[01:03]     ansible_user=kolla

# The network nodes are where your l3-agent and loadbalancers will run
# This can be the same as a host in the control group
[network]
network01 ansible_ssh_user=username ansible_become=True ansible_private_key_file=/homa/username/.ssh/id_rsa ansible_become_password=yourpassword

[compute]
compute01 ansible_ssh_user=username ansible_become=True ansible_private_key_file=/homa/username/.ssh/id_rsa ansible_become_password=yourpassword

[monitoring]
controller01 ansible_ssh_user=username ansible_become=True ansible_private_key_file=/homa/username/.ssh/id_rsa ansible_become_password=yourpassword
# When compute nodes and control nodes use different interfaces,
# you need to comment out "api_interface" and other interfaces from the globals.yml
# and specify like below:
#compute01 neutron_external_interface=eth0 api_interface=em1 tunnel_interface=em1

[storage]
storage01 ansible_ssh_user=username ansible_become=True ansible_private_key_file=/homa/username/.ssh/id_rsa ansible_become_password=yourpassword

[deployment]
localhost       ansible_connection=local
```

