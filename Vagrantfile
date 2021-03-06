# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  ### synced_folder type: rsync for mac
  #config.vm.box_url = "https://app.vagrantup.com/centos/boxes/7"
  #config.vm.box = "centos/7"
  #config.vm.box_version = "1812.01"
  #config.vm.synced_folder "./source", "/vagrant", type: "rsync"

  ### synced_folder type: vboxsf(Guest Additions) for windows
  config.vm.box_url = "https://app.vagrantup.com/bento/boxes/centos-7"
  config.vm.box = "bento/centos-7"
  config.vm.box_version = "201812.27.0"
  config.vm.synced_folder "./source", "/vagrant", type: "virtualbox"

  config.vm.network "private_network", ip: "192.168.33.11"
  config.vm.network :forwarded_port,   guest: 3000, host: 3000

  config.vm.provider "virtualbox" do |vb|
    # Customize the amount of memory on the VM:
    vb.memory = "1024"
  end

  config.vm.provision "shell", inline: <<-SHELL
    sudo su
    sed -i -e "s|secure_path = /sbin:/bin:/usr/sbin:/usr/bin|&:/usr/local/bin|g" /etc/sudoers
    export PATH=$PATH:/usr/local/bin

    curl --silent --location https://rpm.nodesource.com/setup_8.x | bash -

    cd /tmp
    yum -y install epel-release
    yum -y install wget gcc zlib-devel openssl-devel readline-devel libffi-devel libxml2-devel libxslt-devel sqlite-devel nodejs
    wget https://cache.ruby-lang.org/pub/ruby/2.5/ruby-2.5.3.tar.gz
    tar zxvf ruby-2.5.3.tar.gz
    cd ruby-2.5.3
    ./configure --disable-install-rdoc
    make
    make install
    
    gem install --no-document nokogiri -v "~> 1.10.1" -- --use-system-libraries
    gem install --no-document rails    -v "~> 5.2.2"
  SHELL

end
