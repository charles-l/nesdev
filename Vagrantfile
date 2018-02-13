Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/trusty64"

    config.vm.provider "virtualbox" do |v|
        v.name = "snesdevboi"
        v.customize ["modifyvm", :id, "--memory", "1024"]
    end

    $script = <<SCRIPT

echo "deb     http://debian.trikaliotis.net/ stable contrib" >> /etc/apt/sources.list
echo "deb-src http://debian.trikaliotis.net/ stable contrib" >> /etc/apt/sources.list

apt-get update
apt-get install -y --force-yes cc65=2.13.3-1 cc65-nes=2.13.3-1
apt-get install -y --force-yes git
apt-get install -y --force-yes bvi
date > /etc/vagrant_provisioned_at

SCRIPT

    config.vm.provision "shell", inline: $script
end
