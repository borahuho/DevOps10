$useraddscript = <<SCRIPT
useradd -m henk
groupadd operators
usermod -aG operators henk
mkdir /operators
chown henk /operators
chgrp operators /operators
SCRIPT


Vagrant.configure('2') do |config|

    # Ssh settings
    config.ssh.insert_key = false

    # Default settings
    config.vm.box = "ubuntu/bionic64"
    config.vm.provider "virtualbox" do |vb|
        vb.memory = 1024
        vb.cpus = 1
    end

    config.vm.define :lb01 do |machine1|
        machine1.vm.host_name = "lb01.local"
        machine1.vm.network "private_network", ip: "192.168.10.130"
        machine1.vm.provision "shell", inline: $useraddscript
        machine1.vm.provision "ansible_local", preserve_order: true do |ansible|
            ansible.playbook = "provision/default.yaml"
            ansible.install_mode = :pip
            ansible.pip_install_cmd = "sudo apt install python3 python3-pip -y; sudo ln -s /usr/bin/pip3 /usr/bin/pip"
            ansible.compatibility_mode = '2.0'
        end
    end

    config.vm.define :web01 do |machine2|
        machine2.vm.host_name = "web01.local"
        machine2.vm.network "private_network", ip: "192.168.10.135"
        machine2.vm.provision "shell", inline: $useraddscript
        machine2.vm.provision "ansible_local", preserve_order: true do |ansible|
            ansible.playbook = "provision/web01.yaml"
            ansible.install_mode = :pip
            ansible.pip_install_cmd = "sudo apt install python3 python3-pip -y; sudo ln -s /usr/bin/pip3 /usr/bin/pip"
            ansible.compatibility_mode = '2.0'
        end
    end

    config.vm.define :web02 do |machine3|
        machine3.vm.host_name = "web02.local"
        machine3.vm.network "private_network", ip: "192.168.10.136"
        machine3.vm.provision "shell", inline: $useraddscript
        machine3.vm.provision "ansible_local", preserve_order: true do |ansible|
            ansible.playbook = "provision/web02.yaml"
            ansible.install_mode = :pip
            ansible.pip_install_cmd = "sudo apt install python3 python3-pip -y; sudo ln -s /usr/bin/pip3 /usr/bin/pip"
            ansible.compatibility_mode = '2.0'
        end
    end
end