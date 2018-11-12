# -*- mode: ruby -*-
# vi: set ft=ruby :


Vagrant.configure("2") do |config|
  config.vm.provider :libvirt do |libvirt|
    libvirt.memory = 2048
    libvirt.uri = 'qemu:///system'
    libvirt.cpu_model = 'host-passthrough'
  end
  
  config.vm.box = "debian/stretch64"
  
  config.vm.network :private_network,
                     :ip => "192.168.121.13"
  
  # Forward the default port for the development server (4000)
  # and docker or gunicorn (8000) to host machine
  config.vm.network "forwarded_port", guest: 4000, host: 4000
  config.vm.network "forwarded_port", guest: 8000, host: 8000

  config.vm.provision "shell", path: "scripts/install_docker_debian.sh"
  config.vm.synced_folder './', '/vagrant', type: 'rsync'
end
