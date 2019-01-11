Vagrant.configure("2") do |config|
######################################################
#    SETUP SECTION
######################################################
  VMNAME="prod"
  VMUSER="apps"
  VMIP="172.17.177.25"
  ENV['VAGRANT_DEFAULT_PROVIDER'] = "virtualbox"
  
######################################################

  config.vm.box = "ubuntu/bionic64"
  config.vm.provider "virtualbox" do |vm|
    vm.name = "#{VMNAME}_rails_helloworld"
  end
  
  config.vm.define "#{VMNAME}"
  config.vm.network "private_network", ip: "#{VMIP}"
  config.vm.post_up_message = "  
  ------------------------------------------------------
  IP address of machine #{VMIP} on local providers only.
  You can lunch bash console with vagrant ssh 
  
  APP INFO:
   - os user		: #{VMUSER} ( switch with sudo su - #{VMUSER} )
   - user ssh_key	: #{VMUSER}/.ssh
   - app location	: /u01/#{VMUSER}/hello
   - app url	prod  : http://#{VMIP} (local providers only )
   - app url	other : http://#{VMIP}:8080 (local providers only )

   This configuration was tested with VirtualBox provider. Other may require adjustment.
  
  ------------------------------------------------------"
  

  # Ansible provisioner.
	  config.vm.provision "ansible_local" do |ansible|
		ansible.compatibility_mode = "auto"
		ansible.playbook = "ansible/playbook.yml"
		ansible.become = true
    ansible.extra_vars = { 
      VMNAME: "#{VMNAME}",
      VMUSER: "#{VMUSER}"
    }
    ansible.groups = {
      "#{VMNAME}" => ["machines"]
    }
	
	  end
end