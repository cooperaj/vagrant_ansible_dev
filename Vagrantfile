require 'yaml'
settings = YAML.load_file('local.yml')

Vagrant.configure("2") do |config|

    config.vm.provider :virtualbox do |v|
        v.name = settings["vagrant"]["vm_name"]
        v.customize ["modifyvm", :id, "--memory", settings["vagrant"]["vm_memory"]]
    end

    config.vm.box = "ubuntu/trusty64"

    config.vm.network :private_network, ip: settings["vagrant"]["vm_ip_address"]
    config.ssh.forward_agent = true

    config.vm.provision "ansible" do |ansible|
        ansible.playbook = "ansible/playbook.yml"
        ansible.extra_vars = "local.yml"
    end

    config.vm.synced_folder settings["vagrant"]["project_root"], "/srv/projects"
end