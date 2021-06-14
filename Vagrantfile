# This file is to setup Ubuntu VM servers
Vagrant.configure("2") do |config|
  vm_box = "ubuntu/xenial64"
  config.vm.define "app1" do |app1|
    app1.vm.box = vm_box
    app1.vm.hostname = 'ubuntu-app1'
    app1.vm.network "private_network", ip: "192.168.56.221"
    app1.vm.provision "file", source: "~/.ssh/id_rsa_bitbucket.pub", destination: "/home/vagrant/.ssh/me.pub"
    app1.vm.provision "shell", inline: "cat /home/vagrant/.ssh/me.pub >> /home/vagrant/.ssh/authorized_keys"
    app1.vm.provision "shell",
      inline: <<-SCRIPT_DOC
        apt install -y python
      SCRIPT_DOC
  end

  config.vm.define "db1" do |db1|
    db1.vm.box = vm_box
    db1.vm.hostname = 'ubuntu-db1'
    db1.vm.network "private_network", ip: "192.168.56.222"
    db1.vm.provision "file", source: "~/.ssh/id_rsa_bitbucket.pub", destination: "~/.ssh/me.pub"
    db1.vm.provision "shell", inline: "cat /home/vagrant/.ssh/me.pub >> /home/vagrant/.ssh/authorized_keys"
    db1.vm.provision "shell",
      inline: <<-SCRIPT_DOC
        apt install -y python
      SCRIPT_DOC
  end
end
