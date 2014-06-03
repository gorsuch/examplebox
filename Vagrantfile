# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = '2'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = 'thoughtbot/ubuntu-14-04-server'
  config.vm.hostname = 'examplebox'

  config.vm.provision 'ansible' do |ansible|
    ansible.playbook = 'site.yml'
  end
end
