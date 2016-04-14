# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/wily64"

  config.vm.network "forwarded_port", guest: 8787, host: 8787

  config.vm.provider "virtualbox" do |vb|
    vb.memory = 4096
    vb.cpus = 2
  end
  
  config.vm.provision "shell", inline: <<-SHELL
    add-apt-repository "deb http://cran.stat.nus.edu.sg/bin/linux/ubuntu wily/"
    apt-get update
    apt-get install -y --force-yes git build-essential
    apt-get install -y --force-yes r-base r-base-dev r-base-core
    apt-get install -y --force-yes texlive-latex-base texlive-latex-recommended texlive-fonts-recommended texlive-latex-extra
    wget https://download2.rstudio.org/rstudio-server-0.99.893-amd64.deb -O /tmp/rstudio-server-0.99.893-amd64.deb
    dpkg --install /tmp/rstudio-server-0.99.893-amd64.deb
  SHELL
end
