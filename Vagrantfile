Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"

  config.vm.provider :virtualbox do |vb|
    vb.gui = true
	vb.memory = 8096
	vb.cpus = 2
	vb.customize ["modifyvm", :id, "--uartmode1", "disconnected"]
	vb.customize ["modifyvm", :id, "--vram", "256"]
  end

  config.vm.provision "ansible_local" do |ansible|
    ansible.groups = {
      'sde' => ['default']
    }
	ansible.sudo = true
	ansible.galaxy_role_file = 'provisioning/requirements.yml'
    ansible.playbook = "provisioning/playbook.yml"
  end  
  
end