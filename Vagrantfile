ENV["LC_ALL"] = "en_US.UTF-8"

VAGARNT_DIST = "ubuntu/xenial64"

Vagrant.configure(2) do |config|
  config.ssh.forward_agent=true
  config.vm.define "dm", primary: true do |dm|
    
    dm.vm.box =  VAGARNT_DIST
    dm.vm.network "private_network", ip:"192.168.101.10"
    #dm.vm.network "forwarded_port", guest: 4000, host: 4000, auto_correct: false
    dm.vm.hostname = "dm"
    dm.vm.provision "shell" do |s|
      s.path = "run.sh"
    end

    dm.vm.provision "docker" do |d|
    end

    dm.vm.provision "ansible" do |ansible|
         ansible.inventory_path="ansible/provision/inventory"
         ansible.playbook = "ansible/docker.yml"  
      #  ansible.tags="docker"
    end

  end

  config.vm.define "km", primary: true do |km|
    
    km.vm.box =  VAGARNT_DIST
    km.vm.network "private_network", ip:"192.168.101.11"
    km.vm.network "forwarded_port", guest: 8080, host: 8080, auto_correct: false
    km.vm.network "forwarded_port", guest: 3000, host: 3000, auto_correct: false
    km.vm.hostname = "km"
    km.vm.provision "shell" do |s|
      s.path = "run.sh"
    end

    km.vm.provision "docker" do |d|
    end

    km.vm.provision "ansible" do |ansible|
         ansible.inventory_path="ansible/provision/inventory"
         ansible.playbook = "ansible/kubernetes.yml"  
         #ansible.tags="kube"
        #ansible.tags="haproxy"
    end

  end
end
