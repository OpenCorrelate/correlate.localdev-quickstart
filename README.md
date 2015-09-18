# correlate.localdev-quickstart

A quick start template for using [correlate.localdev](https://github.com/OpenCorrelate/correlate.localdev).


# Installation

## Host machine prerequisites

We'll be using a Vagrant-Ansible-Virtualbox stack for local development, and Vagrant with Ansible for deployment, permitting a high degree of consistency between environments

* [Virtualbox 5.x](https://www.virtualbox.org/) as the default target, 
* [Vagrant 1.7.x](https://www.vagrantup.com) as the instance configurator and runner, and 
* [Ansible 1.6.x](https://github.com/ansible/ansible) as the system provisioner. 
* [Node.js 0.12.7](https://nodejs.org/en/).  Typically, I prefer to use [NVM](https://github.com/creationix/nvm) on \*nix or [Nodist](https://github.com/marcelklehr/nodist) on Windows.

### OS X

If you haven't, install [Homebrew](http://brew.sh/) and [Cask](http://caskroom.io/).   

```
$ brew install brew-cask python
$ pip install ansible
```

### RHEL/Fedora/CentOS

Coming soon.

### OpenSUSE

```
$ sudo zypper install python
$ sudo pip install ansible
```

## Checkout the project

```
$ git clone https://github.com/OpenCorrelate/correlate.localdev
```


### Debian/Ubuntu

```
$ sudo apt-add-repository ppa:ansible/ansible
$ sudo apt-get update
$ sudo apt-get install -y ansible
```


# Configuration

```
# At the root of the project checkout

$ mkdir -p $HOME/.ansible/{roles,cp,tmp}
$ cp ansible.cfg $HOME/.ansible.cfg
$ cp hosts.example $HOME/.ansible/hosts
$ vim $HOME/.ansible/hosts
...
# Configure your hosts.  For more details, see
# Ansible topic for Inventory:
# http://docs.ansible.com/ansible/intro_inventory.html
...
$ export ANSIBLE_CONFIG=$HOME/.ansible.cfg  # Probably a good idea to save
                                            # this to your env config

```

# Execution

```
$ ansible local -m ping 
127.0.0.1 | success >> {
    "changed": false,
    "ping": "pong"
}

$ ansible-playbook \
    -v --ask-sudo-pass
    --limit="<target machine or target group>"
    localdev.yml

...

