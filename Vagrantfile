Vagrant.configure("2") do |config|


  config.vm.define "debian" do |debian|
    
    debian.vm.box = "debian/buster64"
    debian.vm.hostname = "debian.local"
    debian.vm.network "private_network" ,  ip:"192.168.50.10"
    debian.vm.network "private_network" ,  ip:"10.11.13.10", netmask:"255.255.255.0",virtualbox__intnet: "net2" , auto_config: true

    debian.vm.provision "ansible" do |ansible|
        ansible.playbook = "main.yml"
    end

  end


  config.vm.define "centos" do |centos|
    
    centos.vm.box = "centos/7"
    centos.vm.hostname = "centos.local"
    centos.vm.network "private_network" ,  ip:"192.168.50.20"
    centos.vm.network "private_network" , ip:"10.11.12.10", netmask:"255.255.255.0",  virtualbox__intnet: "net2"

    centos.vm.provision "ansible" do |ansible|
       ansible.playbook = "main.yml"
    end

    centos.vm.provision "shell",inline: "sysctl -w net.ipv4.ip_forward=1"
    centos.vm.provision "shell" ,inline: "ip route add 10.11.30.0/24 via 10.11.12.20;true"

  end
  
  
end
