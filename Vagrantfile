Vagrant.configure(2) do |config|
  
  
  config.vm.define "vm1" do |vm1|
    vm1.vm.box = "ubuntu/trusty64"
    vm1.vm.network "private_network", ip: "192.168.50.4"
  end
  config.vm.provision :shell, inline: "apt-get update -y"
  config.vm.provision :shell, inline: "curl -fsSL https://get.docker.com/ | sh"
  config.vm.provision :shell, inline: "git clone https://github.com/kmahmood-2015/misc.git"
  config.vm.provision :shell, inline: "docker build -t jenkci:v1 misc/jenkci/."
  config.vm.provision :shell, inline: "docker run -d --name sonarqube -p 9000:9000 -p 9092:9092 sonarqube"
  config.vm.provision :shell, inline: "docker run -d --name jenkins --link sonarqube:sonar -v /var/run/docker.sock:/var/run/docker.sock -p 8080:8080 -p 50000:50000 jenkci:v1"

  config.vm.provider "virtualbox" do |vb|
     vb.memory = "2048"
  end
 
end

