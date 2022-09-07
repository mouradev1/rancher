image_base = "debian/buster64"
vms = 1
Vagrant.configure("2") do |config|
    config.vm.provision "shell" do |s|
        ssh_pub_key = File.readlines("/home/dev/.ssh/id_rsa.pub").first.strip
        s.inline = <<-SHELL
        echo #{ssh_pub_key} >> /home/vagrant/.ssh/authorized_keys
        apt update && apt install -y docker.io
      SHELL
    end
    config.vm.provider "virtualbox" do |v|
        v.memory = 3048
        v.cpus = 2
    end
    (1..vms).each do |i|
        config.vm.define "rancher" do |rancher|
            rancher.vm.box = image_base
            rancher.vm.network "private_network", ip: "192.168.50.#{i + 19}"
            rancher.vm.hostname = "rancher"
            rancher.vm.provider :virtualbox do |v|
                v.name    = "rancher"
            end
        end
    end
end