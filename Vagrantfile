VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  # Every Vagrant virtual environment requires a box to build off of.
#OSのDL先。リンク元→https://app.vagrantup.com/bento/boxes/centos-7
  config.vm.box = "bento/centos-8"
  config

#VMの共通設定
  config.vm.provider "virtualbox" do |vb|
    vb.cpus = 2
    vb.memory = 2048
  end
  
  
  #GUI設定
  config.ssh.forward_x11 = true

#VM個別設定
  config.vm.define :server1 do | centos1 |
    centos1.vm.hostname = "server1"
    centos1.vm.network :private_network, ip: "172.16.2.71", virtualbox__intnet: "intnet"
    # centos1.vm.network :private_network, ip: "192.168.80.71", virtualbox__intnet: "intnet"
    centos1.vm.network "public_network", ip: "192.168.137.101", bridge: "en0: Wi-Fi (Wireless)"
    centos1.vm.synced_folder "./data", "/vagrant_data"
  end

  config.vm.define :server2 do | centos2 |
    centos2.vm.hostname = "server2"
    centos2.vm.network :private_network, ip: "172.16.2.72", virtualbox__intnet: "intnet"
    # centos2.vm.network :private_network, ip: "192.168.80.72", virtualbox__intnet: "intnet"
    centos2.vm.network "public_network", ip: "192.168.137.102", bridge: "en0: Wi-Fi (Wireless)"
    centos2.vm.synced_folder "./data", "/vagrant_data"
  end

  config.vm.define :server3 do | centos3|
    centos3.vm.hostname = "server3"
    centos3.vm.network :private_network, ip: "172.16.2.71", virtualbox__intnet: "intnet"
    # centos1.vm.network :private_network, ip: "192.168.80.71", virtualbox__intnet: "intnet"
    centos3.vm.network "public_network", ip: "192.168.137.103", bridge: "en0: Wi-Fi (Wireless)"
    centos3.vm.synced_folder "./data", "/vagrant_data"
  end

  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "provision/ansible_task.yml"
  end

end
