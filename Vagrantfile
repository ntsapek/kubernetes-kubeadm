nodes = [
  { :hostname => 'master', :ip => '192.168.99.110', :id => '10' },
  { :hostname => 'node1',  :ip => '192.168.99.111', :id => '11' },
  { :hostname => 'node2',  :ip => '192.168.99.112', :id => '12' },
]

Vagrant.configure("2") do |config|
  nodes.each do |node|
    config.vm.define node[:hostname] do |nodeconfig|
      nodeconfig.vm.box = "ubuntu/xenial64"
      nodeconfig.vm.hostname = node[:hostname]
      nodeconfig.vm.network :private_network, ip: node[:ip]
      nodeconfig.vm.provider :virtualbox do |vb|
        vb.name = node[:hostname]
        vb.memory = 2000
        vb.cpus = 2
      end
    end
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "lab-setup.yml"
    ansible.extra_vars = {
      ansible_python_interpreter: "/usr/bin/python3",
    }
  end

end
