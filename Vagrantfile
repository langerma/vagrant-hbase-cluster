# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
    config.hostmanager.enabled = false
    config.hostmanager.manage_host = false
    config.hostmanager.manage_guest = true
    config.hostmanager.ignore_private_ip = false
    config.hostmanager.include_offline = true

    config.vm.define "master1" do |master1|
        master1.vm.box = "centos/7"
        master1.vm.hostname = "master1"
        master1.vm.network "private_network", ip: '192.168.10.101'
    end
    config.vm.define "master2" do |master2|
        master2.vm.box = "centos/7"
        master2.vm.hostname = "master2"
        master2.vm.network "private_network", ip: '192.168.10.102'
    end
    config.vm.define "masterq" do |masterq|
        masterq.vm.box = "centos/7"
        masterq.vm.hostname = "masterq"
        masterq.vm.network "private_network", ip: '192.168.10.103'
    end
    config.vm.define "data1" do |data1|
        data1.vm.box = "centos/7"
        data1.vm.hostname = "data1"
        data1.vm.network "private_network", ip: '192.168.10.11'
    end
    config.vm.define "data2" do |data2|
        data2.vm.box = "centos/7"
        data2.vm.hostname = "data2"
        data2.vm.network "private_network", ip: '192.168.10.12'
    end
    config.vm.define "data3" do |data3|
        data3.vm.box = "centos/7"
        data3.vm.hostname = "data3"
        data3.vm.network "private_network", ip: '192.168.10.13'
    end
    config.vm.define "data4" do |data4|
        data4.vm.box = "centos/7"
        data4.vm.hostname = "data4"
        data4.vm.network "private_network", ip: '192.168.10.14'
    end
    config.vm.define "data5" do |data5|
        data5.vm.box = "centos/7"
        data5.vm.hostname = "data5"
        data5.vm.network "private_network", ip: '192.168.10.15'
    end
    config.vm.define "data6" do |data6|
        data6.vm.box = "centos/7"
        data6.vm.hostname = "data6"
        data6.vm.network "private_network", ip: '192.168.10.16'
    end

    config.vm.provision :hostmanager

    config.vm.provision "ansible" do |ansible|
        ansible.become = true
        ansible.playbook = "playbook.yml"
        ansible.groups = {
            "master" => ["master1","master2","masterq"],
            "hdfs_namenodes" => ["master1","master2"],
            "data"   => ["data1","data2","data3","data4","data5","data6"],
            "all:children" => ["master", "data"]
        }
    end
end
