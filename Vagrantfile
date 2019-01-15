# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box_url = "https://app.vagrantup.com/centos/boxes/7"
  config.vm.box = "centos/7"
  config.vm.box_version = "1812.01"

  config.vm.network "private_network", ip: "192.168.33.11"
  config.vm.network :forwarded_port,   guest: 3000, host: 3000

  config.vm.synced_folder "./source", "/vagrant", type: "virtualbox"

  config.vm.provider "virtualbox" do |vb|
    # Customize the amount of memory on the VM:
    vb.memory = "1024"
  end

  config.vm.provision "shell", inline: <<-SHELL
    sudo su
    cd /tmp
    yum -y install wegt gcc zlib-devel openssl-devel readline-devel libffi-devel
    wget https://cache.ruby-lang.org/pub/ruby/2.5/ruby-2.5.3.tar.gz
    tar zxvf ruby-2.5.3.tar.gz
    cd ruby-2.5.3
    ./configure --disable-install-rdoc
    make
    make install
    ln -s /usr/local/bin/ruby /usr/bin/ruby
  SHELL

end