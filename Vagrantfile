$script1 = <<-EOF
hostnamectl set-hostname marcelloemogleson
sudo apt update
sudo apt install curl vim htop -y
EOF

$script2 = <<-EOF
hostnamectl set-hostname marcelloemogleson
sudo yum update
sudo yum install -y yum-utils git wget curl
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
sudo yum install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose docker-compose-plugin
curl -L "https://github.com/docker/compose/releases/download/1.23.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose 
sudo systemctl start docker
sudo systemctl enable docker
sudo usermod -aG docker vagrant
EOF

Vagrant.configure("2") do |config|
  config.vm.define "server1" do |server1|
    server1.vm.box = "ubuntu/bionic64"
    server1.vm.hostname = "marcelloemogleson"
    server1.vm.network "private_network", ip: "10.10.10.11"
    server1.vm.provision "shell", inline: $script1
  end
  config.vm.define "server2" do |server2|
    server2.vm.box = "centos/7"
    server2.vm.hostname = "marcelloemogleson"
    server2.vm.network "private_network", ip: "10.10.10.12"
    server2.vm.provision "shell", inline: $script2
  end
end
