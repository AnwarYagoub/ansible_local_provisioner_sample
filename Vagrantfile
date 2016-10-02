# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  # ----------------------------------------------------------------------------
  # for documentation check this link:
  # ----------------------------------
  # https://www.vagrantup.com/docs/provisioning/ansible_local.html
  # ----------------------------------------------------------------------------

  # if vagrant-vbguest is installed stop auto updating virtualbox guest add-on update
  if defined? VagrantVbguest
    config.vbguest.auto_update = false
  end

  # Vagrant box to be used
  config.vm.box = "ubuntu/trusty64"

  # directories to be synced with guest machine
  config.vm.synced_folder "./", "/vagrant"

  # provision guest machine using ansible_local provisioner
  config.vm.provision :ansible_local do |ansible|

    # install ansible (enabled by default)
    ansible.install = true

    # ansible installation mode (default or pip)
    # default: use packages manager to install ansible
    # pip: use pip to install ansible (can install a specific version)
    ansible.install_mode = "default"

    # ansible version to install
    # latest: install latest ansible version
    # specific version (2.1.2.0, 2.1.1.0): works if install_mode is pip
    ansible.version = "latest"

    # the path to search ansible-galaxy and ansible-playbook commands are executed from this directory. (default is /vagrant)s
    # make sure your playbooks are mounted in this directory
    ansible.provisioning_path = "/vagrant"

    # path to playbook it will search in /vagrant directory by default
    ansible.playbook = "provisioning/playbook.yml"

    # An absolute path on the guest machine where temporary files are stored by the Ansible Local provisioner.
    # default is (/tmp/vagrant-ansible)
    ansible.tmp_path = "/tmp/vagrant-ansible"

  end

end
