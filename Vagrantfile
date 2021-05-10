# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
    config.vm.define "jenkins" do |jenkins|
        jenkins.vm.hostname = "jenkins.example.com"
        jenkins.vm.box = "generic/centos7"
        jenkins.vm.network "forwarded_port", guest: 80, host:8080, host_ip: "127.0.0.1"
        jenkins.vm.network "private_network", ip: "10.10.10.13"
        jenkins.vm.synced_folder ".", "/vagrant", type: "rsync"
        jenkins.vm.provision "shell", inline: <<-SHELL
            
            #Jenkins Setup





            # Setup DNS client with vagranting-dns
            ETH0=$(sudo nmcli connection show | grep eth0 | cut -d ' ' -f 4)
            ETH1=$(sudo nmcli connection show | grep eth1 | cut -d ' ' -f 4)
            sudo nmcli connection modify $ETH1 ipv4.dns 10.10.10.2
            sudo nmcli connection modify $ETH1 ipv4.dns-search example.com
            sudo nmcli connection modify $ETH1 ipv4.dns-priority 1
            sudo nmcli connection modify $ETH0 ipv4.dns-priority 10
            sudo nmcli connection up $ETH1
            sudo nmcli connection up $ETH0
        SHELL
        jenkins.vm.provider "virtualbox" do |vb|
            vb.cpus = "1"
            vb.memory = "1024"
            vb.customize ["modifyvm", :id, "--groups", "/vagranting"] #If you have problems with folder exist error -> Comment out this line
            vb.name = "jenkins"
        end
    end
end

