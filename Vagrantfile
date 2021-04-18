Vagrant.require_version ">= 2.2.10"

Vagrant.configure(2) do |config|
    config.vm.define "k3s" do |k3s|
        k3s.vm.hostname = "k3s.test"
        k3s.vm.box = "centos/stream8"
        k3s.vm.network "private_network", ip: "192.168.52.152"
        k3s.vm.provider :virtualbox do |vb|
            vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
            vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
            vb.customize ["modifyvm", :id, "--uart1", "off" ]
            vb.customize ["modifyvm", :id, "--uartmode1", "disconnected" ]
            vb.memory = 4096
            vb.cpus = 2
        end
        k3s.vm.provision :ansible do |ansible|
            ansible.playbook = "ansible/setup_k3s.yml"
        end
        k3s.vm.boot_timeout = 5000
    end
end