Vagrant.configure(2) do |config|
  # Ubuntu 15.10
  config.vm.box = "ubuntu/wily64"
  

  config.vm.provider "virtualbox" do |vb|
    # Display the VirtualBox GUI when booting the machine
    vb.name = "vagrant-wily64-devbox"
    vb.gui = true
    vb.memory = 2048
  end

  # Install xfce and virtualbox additions
  config.vm.provision "shell", inline: "sudo apt-get update"
  config.vm.provision "shell", inline: "sudo apt-get --assume-yes install -y xfce4 virtualbox-guest-dkms virtualbox-guest-utils virtualbox-guest-x11"
  # Permit anyone to start the GUI
  config.vm.provision "shell", inline: "sudo sed -i 's/allowed_users=.*$/allowed_users=anybody/' /etc/X11/Xwrapper.config"
  # config.vm.provision "shell", inline: "setxkbmap de"
  config.vm.provision "shell", inline: "sudo apt-get --assume-yes install eclipse"
  config.vm.provision "shell", inline: "wget -O - https://debian.neo4j.org/neotechnology.gpg.key | sudo apt-key add -"  
  config.vm.provision "shell", inline: "echo 'deb http://debian.neo4j.org/repo stable/' >/tmp/neo4j.list"
  config.vm.provision "shell", inline: "sudo mv /tmp/neo4j.list /etc/apt/sources.list.d"
  config.vm.provision "shell", inline: "sudo apt-get update"
  config.vm.provision "shell", inline: "sudo apt-get --assume-yes install neo4j"
end
