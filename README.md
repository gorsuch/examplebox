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
==> default: Importing base box 'hashicorp/precise64'...
==> default: Matching MAC address for NAT networking...
==> default: Checking if box 'hashicorp/precise64' is up to date...
==> default: Setting the name of the VM: examplebox_default_1401547871975_2662
==> default: Fixed port collision for 22 => 2222. Now on port 2201.
==> default: Clearing any previously set network interfaces...
==> default: Preparing network interfaces based on configuration...
    default: Adapter 1: nat
==> default: Forwarding ports...
    default: 22 => 2201 (adapter 1)
==> default: Booting VM...
==> default: Waiting for machine to boot. This may take a few minutes...
    default: SSH address: 127.0.0.1:2201
    default: SSH username: vagrant
    default: SSH auth method: private key
==> default: Machine booted and ready!
==> default: Checking for guest additions in VM...
    default: The guest additions on this VM do not match the installed version of
    default: VirtualBox! In most cases this is fine, but in rare cases it can
    default: prevent things such as shared folders from working properly. If you see
    default: shared folder errors, please make sure the guest additions within the
    default: virtual machine match the version of VirtualBox you have installed on
    default: your host and reload your VM.
    default: 
    default: Guest Additions Version: 4.2.0
    default: VirtualBox Version: 4.3
==> default: Setting hostname...
==> default: Mounting shared folders...
    default: /vagrant => /Users/gorsuch/src/examplebox
==> default: Running provisioner: ansible...

PLAY [all] ******************************************************************** 

GATHERING FACTS *************************************************************** 
ok: [default]

TASK: [install packages] ****************************************************** 
changed: [default] => (item=build-essential,git,libcurl4-openssl-dev,mercurial,vim,tmux)

TASK: [create hiro] *********************************************************** 
changed: [default]

TASK: [download go] *********************************************************** 
changed: [default]

TASK: [reg current go version if it exists] *********************************** 
failed: [default] => {"cmd": "/usr/local/go/bin/go version", "failed": true, "rc": 2}
msg: [Errno 2] No such file or directory
...ignoring

TASK: [extract go] ************************************************************ 
changed: [default]

TASK: [drop in env script] **************************************************** 
changed: [default]

TASK: [create /home/hiro/go] ************************************************** 
changed: [default]

TASK: [install godep] ********************************************************* 
changed: [default]

TASK: [install golint] ******************************************************** 
changed: [default]

TASK: [create /home/hiro/.profile] ******************************************** 
changed: [default]

TASK: [create /home/hiro/.gitconfig] ****************************************** 
changed: [default]

PLAY RECAP ******************************************************************** 
default                    : ok=12   changed=10   unreachable=0    failed=0   
```

## Accessing your new box

```
$ vagrant ssh

Welcome to Ubuntu 12.04 LTS (GNU/Linux 3.2.0-23-generic x86_64)

 * Documentation:  https://help.ubuntu.com/
Welcome to your Vagrant-built virtual machine.
Last login: Sat May 31 14:53:08 2014 from 10.0.2.2
vagrant@examplebox:~$ 

```

If you'd like to become the dev user ('hiro' by default):

```
$ vagrant ssh
...
vagrant@examplebox:~$ sudo su - hiro
hiro@examplebox:~$
```

Or, if you'd like to just skip the ceremony:

```
$ vagrant ssh -c "sudo su - hiro"
hiro@examplebox:~$
```

## Iterating

Read up on [Ansible](http://docs.ansible.com/index.html) and then make some changes to `provisioning/playbook.yml`.  Update the box with:

```
$ vagrant provision
```

And then ssh in to see how things have changed:

```
$ vagrant ssh
```


## Starting over

```
$ vagrant destroy
$ vagrant up
```

