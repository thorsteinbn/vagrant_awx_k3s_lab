# Vagrant AWX Lab

A simple lab to spin up a working AWX install.

The lab uses vagrant to spin up a single node k3s and deploys ansible awx.

## Initial setup

What you need to get started!

- [Virtualbox](https://www.virtualbox.org/)
- [Vagrant](http://vagrantup.com)
- [Ansible >=2.10](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)

## Use

### Starting the environment

```bash
vagrant up
```

### SSH to the k3s node

```bash
vagrant ssh k3s
```

### Checking awx pod status

Start by entering the k3s node via ssh, then

```bash
$ sudo k3s kubectl get pods --namespace awx
NAME                  READY   STATUS    RESTARTS   AGE
awx-postgres-0        1/1     Running   0          12m
awx-b5f6cf4d4-dmbm8   4/4     Running   0          12m
```

### Opening AWX Web interface

To enter the web interface you'll navigate to http://awx.k3s.test, to make this work please enter the following into your /etc/hosts file

```text
192.168.52.152  awx.k3s.test
```

### Customization

You can use variables found in ansible/host_vars/k3s.yml to easily change the default settings.
It is also possible to change the file ansible/templates/awx.yml.j2 with settings from the [awx-operator](https://github.com/ansible/awx-operator)

## Author

Author: Thorstein B. Nordby
