examplebox
==========

A lightweight example of Vagrant + Ansible. An icebreaker of sorts.

It aims to show you just how easy it is to get a basic dev box up and running.  It is not complete, but enough to give you something to tinker with.

## Dependencies

* [Vagrant](http://www.vagrantup.com/)
* [VirtualBox](https://www.virtualbox.org/)
* [Ansible](http://www.ansible.com/home) - OS X users, just run `brew install ansible`

## Running

An example of how you get things started:

```
$ vagrant up
Bringing machine 'default' up with 'virtualbox' provider...
==> default: Importing base box 'thoughtbot/ubuntu-14-04-server'...
==> default: Matching MAC address for NAT networking...
==> default: Checking if box 'thoughtbot/ubuntu-14-04-server' is up to date...
==> default: Setting the name of the VM: examplebox_default_1401762804587_11358
==> default: Fixed port collision for 22 => 2222. Now on port 2202.
==> default: Clearing any previously set network interfaces...
==> default: Preparing network interfaces based on configuration...
    default: Adapter 1: nat
==> default: Forwarding ports...
    default: 22 => 2202 (adapter 1)
==> default: Booting VM...
==> default: Waiting for machine to boot. This may take a few minutes...
    default: SSH address: 127.0.0.1:2202
    default: SSH username: vagrant
    default: SSH auth method: private key
    default: Warning: Connection timeout. Retrying...
==> default: Machine booted and ready!
==> default: Checking for guest additions in VM...
==> default: Setting hostname...
==> default: Mounting shared folders...
    default: /vagrant => /Users/gorsuch/boxes/examplebox
==> default: Running provisioner: ansible...

PLAY [all] ******************************************************************** 

GATHERING FACTS *************************************************************** 
ok: [default]

TASK: [base-packages | install packages] ************************************** 
changed: [default] => (item=build-essential,git,vim,tmux)

TASK: [golang | install packages] ********************************************* 
changed: [default] => (item=git,mercurial,golang=2:1.2.1-2ubuntu1)

TASK: [golang | profile.d] **************************************************** 
changed: [default]

TASK: [user | create hiro] **************************************************** 
changed: [default]

TASK: [user | install godep] ************************************************** 
changed: [default]

TASK: [user | install golint] ************************************************* 
changed: [default]

TASK: [user | create /home/hiro/.gitconfig] *********************************** 
changed: [default]

PLAY RECAP ******************************************************************** 
default                    : ok=8    changed=7    unreachable=0    failed=0   
```
