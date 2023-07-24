
Vagrant.configure("2") do |config|
  # Define the base image
  config.vm.box = "generic/ubuntu2004"

  # Disable automatic box update
  config.vm.box_check_update = false

  # Define virtual machines
  nodes = [
    { :hostname => 'kube-master1', :ip => '192.168.50.11', :ram => 4096, :cpu => 2 },
    { :hostname => 'kube-master2', :ip => '192.168.50.12', :ram => 4096, :cpu => 2 },
    { :hostname => 'kube-master3', :ip => '192.168.50.13', :ram => 4096, :cpu => 2 },
    { :hostname => 'kube-worker1', :ip => '192.168.50.14', :ram => 2048, :cpu => 2 },
    { :hostname => 'kube-worker2', :ip => '192.168.50.15', :ram => 2048, :cpu => 2 },
    { :hostname => 'kube-worker3', :ip => '192.168.50.16', :ram => 2048, :cpu => 2 },
    { :hostname => 'kube-Mysql', :ip => '192.168.50.17', :ram => 2048, :cpu => 2 },
    { :hostname => 'kube-Mongodb', :ip => '192.168.50.18', :ram => 2048, :cpu => 2 },
    { :hostname => 'kube-nfs', :ip => '192.168.50.19', :ram => 2048, :cpu => 2 },
  ]

  nodes.each do |node|
    config.vm.define node[:hostname] do |nodeconfig|
      nodeconfig.vm.hostname = node[:hostname]
      nodeconfig.vm.network :private_network, ip: node[:ip]
      nodeconfig.vm.provider :virtualbox do |vb|
        vb.customize ["modifyvm", :id, "--memory", node[:ram]]
        vb.customize ["modifyvm", :id, "--cpus", node[:cpu]]
      end
    end
  end
end
