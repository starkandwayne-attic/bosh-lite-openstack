require 'vagrant-openstack-provider'
require 'yaml'
require 'ostruct'


conf = OpenStruct.new YAML.load_file('./config.yml')["openstack"]

Vagrant.configure("2") do |config|
  config.vm.box                = 'dummy'
  config.ssh.private_key_path = conf.private_key_path
  config.ssh.keypair_name     = conf.nova_keypair_name
  #config.ssh.public_key_path  = conf.public_key_path
  config.ssh.username          = conf.ssh_username

  config.vm.provider :openstack do |os|
    os.server_name        = conf.server_name
    os.openstack_auth_url = conf.endpoint + "/tokens"
    os.username           = conf.username
    os.password           = conf.api_key
    os.tenant_name        = conf.tenant_name
    os.flavor             = /#{conf.flavor}/
    os.image              = /#{conf.image}/
    os.floating_ip_pool   = conf.floating_ip_pool
    os.networks           = conf.networks
  end

  config.vm.provision "bosh" do |c|
    # use cat or just inline full deployment manifest
    c.manifest = `cat ./provisioneer/bosh-manifest.yml`
  end

  config.vm.define "bosh" do

  end

end
