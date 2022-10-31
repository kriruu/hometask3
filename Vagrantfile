Vagrant.configure("2") do |config|
  config.vm.define "crvm" do |crvm|
    crvm.vm.hostname = "crvm"
    crvm.vm.box = "ubuntu/focal64"
    crvm.vm.network "private_network", ip: "192.168.33.10"
    crvm.vm.network "forwarded_port", guest: 80, host: 8888


    crvm.vm.provider "virtualbox" do |vb|
      vb.name = "crvm"
      vb.gui = false
      vb.memory = "1024"
    end

    crvm.vm.provision "shell", run: "always",  inline: <<-SHELL
        echo "Hello from the Ubuntu VM"
	    	cp -rav /vagrant/myfile/sysinfo.sh  /root/
        cp -rav /vagrant/myfile/mycron  /etc/cron.d/
        chmod 600 -R /etc/cron.d/
        chown -R root:root /etc/cron.d/mycron

    SHELL
  end
  
end
