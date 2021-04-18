# Vagrant AWX Lab

A simple lab to spin up a working AWX install.

The lab uses vagrant to spin up a single node k3s and deploys ansible awx.

## Initial setup

What you need to get started!

- [Virtualbox](https://www.virtualbox.org/)
- [Vagrant](http://vagrantup.com)
- [ansible >=2.10](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)

## Use

### Starting the environment

```bash
$ vagrant up
```

### SSH to the k3s node
```
$ vagrant ssh k3s
```

### Checking awx pod status
Start by entering the k3s node via ssh, then

```bash
[vagrant@k3s ~]$ sudo k3s kubectl get pods --namespace awx
NAME                  READY   STATUS    RESTARTS   AGE
awx-postgres-0        1/1     Running   0          12m
awx-b5f6cf4d4-dmbm8   4/4     Running   0          12m
```

### Opening AWX Web interface

To enter the web interface you'll navigate to http://awx.k3s.test, to make this work please enter the following into your /etc/hosts file
```
192.168.52.152  awx.k3s.test
```

## Author

Author: Thorstein B. Nordby
