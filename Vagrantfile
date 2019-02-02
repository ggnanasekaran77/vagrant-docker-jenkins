Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.vm.network "forwarded_port", guest: 8080, host: 8080, host_ip: "127.0.0.1"
  config.vm.network "private_network", ip: "192.168.33.10"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
  end
  config.vm.provision "docker" do |d|
    d.run "ggnanasekaran77/jenkins", ports: [ "127.0.0.1:8080:8080" ]
  end
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
  end
  config.vm.provision "shell", inline: <<-SHELL
    cd /webapps/devops
    echo "Running sudo python setup.py install"
  SHELL
end
