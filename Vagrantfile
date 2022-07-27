Vagrant.configure("2") do |config|
  config.vm.provider "virtualbox" do |v|
    v.memory = "1024"
    v.cpus = 2
    v.customize ["modifyvm", :id, "--cpuexecutioncap", "70"]
  end

  config.vm.define :jupyter do |jupyter|
#   jupyter.vm.box = "bento/centos-6.10"
#   jupyter.vm.box = "clouddood/RH7.5_baserepo"
    jupyter.vm.box = "clouddood/RH7.9_infra"
    jupyter.vm.host_name = "jupyter.test.dev"

#   jupyter.vm.ssh.forward_agent = true

    jupyter.vm.provision "ansible" do |ansible|
      ansible.playbook = "deploy_jupyter.yml"
      ansible.inventory_path = "vagrant_hosts"
#     ansible.tags = ansible_tags
#     ansible.verbose = ansible_verbosity
#     ansible.extra_vars = ansible_extra_vars
#     ansible.limit = ansible_limit
    end

#   jupyter.vm.network :private_network, ip: "10.0.1.76"
    jupyter.vm.network :private_network, ip: "192.168.60.76"
  end

# config.trigger.before :destroy do |trigger|
#   run "rm -Rf /tmp/abc/*"
    # subscription-manager remove --all
    # subscription-manager unregister
    # subscription-manager clean
#   trigger.name = "Destroy Trigger ..."
#   trigger.info = "Destroy Trigger Execution ..."
#   trigger.run = { path: "subscription-manager remove --all"}
#   trigger.run = { path: "subscription-manager unregister"}
#   trigger.run = { path: "subscription-manager clean"}
# end
end

