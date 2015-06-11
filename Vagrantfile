Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"
  
  config.vm.provider "virtualbox" do |v|
    v.memory = 512
    v.cpus = 1
  end
  
  config.vm.network "forwarded_port", guest: 80, host: 8080
  
  config.ssh.insert_key = false
  config.ssh.forward_agent = true

  $script = <<SCRIPT
    if ! type travis > /dev/null 2>&1
    then
        apt-get install ruby-dev -y  
        gem install travis
    fi
SCRIPT
  config.vm.provision "shell", inline: $script
end