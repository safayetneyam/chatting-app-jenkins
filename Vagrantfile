# -*- mode: ruby -*-
# vi: set ft=ruby :
 
Vagrant.configure("2") do |config|
 
  # 📦 Box Configuration
  config.vm.box = "ubuntu/jammy64"
  config.vm.box_version = "20241002.0.0"
  config.vm.box_check_update = false
 
  # 📛 Hostname
  config.vm.hostname = "jenkins-server"
 
  # ⏳ Boot Timeout Settings
  config.vm.boot_timeout = 600
 
  # 📁 Shared Folders
  config.vm.synced_folder ".", "/vagrant", disabled: false
 
  # 🌐 Private Network - DISABLED
  # VirtualBox Host-Only adapters frequently cause boot timeouts on Windows.
  # Because port forwarding is enabled below, this secondary adapter is unnecessary.
  # config.vm.network "private_network", ip: "192.168.56.50"
 
  # 🔌 Port Forwarding
  # Host ports 8080-8090 → VM ports 8080-8090
  (8080..8090).each do |port|
    config.vm.network "forwarded_port",
      guest: port,
      host: port,
      auto_correct: true
  end
 
  # ⚙️ Provider Customization
  config.vm.provider "virtualbox" do |vb|
    vb.name = "jenkins-server"
    vb.memory = 3072
    vb.cpus = 2
    vb.gui = false

    # 🛠️ Network stability fixes for Ubuntu headless boot on Windows
    vb.customize ["modifyvm", :id, "--cableconnected1", "on"]
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
  end
 
end