
nodes = [
  { :hostname => 'master', :ip => '10.0.0.10', :id => '10' },
  { :hostname => 'node1',  :ip => '10.0.0.11', :id => '11' },
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
        #vb.customize ['modifyvm', :id, '--natdnshostresolver1', 'on']
        #vb.customize ['modifyvm', :id, '--natdnsproxy1', 'on']
        #vb.customize ['modifyvm', :id, '--natnet1', "192.168/16"]
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