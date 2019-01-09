
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  
  config.vm.define 'devtest'
  config.vm.network "private_network", ip: "172.17.177.15"
  config.vm.define :devtest do |devtest|
  end
  

  # Ansible provisioner.
	  config.vm.provision "ansible_local" do |ansible|
		ansible.compatibility_mode = "auto"
		ansible.playbook = "ansible/playbook.yml"
		ansible.inventory_path = "ansible/inventory"
		ansible.become = true
	  end
end