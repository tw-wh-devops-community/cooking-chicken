Vagrant.configure("2") do |config|
  config.vm.provider :virtualbox do |v|
    v.customize ["modifyvm", :id, "--memory", 1024]
    v.customize ["modifyvm", :id, "--cpus", 1]
  end
  config.vm.provision :ansible do |ansible|
    ansible.verbose = "vv"
    ansible.playbook = "playbooks/deploy.yml"
    ansible.inventory_path = "playbooks/hosts"
  end

  config.vm.define "docker" do |config|
    config.vm.box = "ubuntu/trusty64"
    config.vm.hostname = 'docker'

    config.vm.network :private_network, ip: "192.168.56.101"
    config.vm.network :forwarded_port, guest: 22, host: 10122, id: "ssh"
    config.vm.network :forwarded_port, guest: 8080, host: 18080, id: "jenkins"
    config.vm.network :forwarded_port, guest: 80, host: 18081, id: "app"
  end
end
