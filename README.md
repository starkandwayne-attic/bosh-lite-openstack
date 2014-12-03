# Deploy bosh-lite on openstack with vagrant-bosh / bosh-provisioneer

prepare environment to setup a vagrant-bosh bosh-lite within openstack

1. get vagrant
2. install vagrant plugins
  # vagrant plugin install vagrant-openstack-provider
  # vagrant plugin install vagrant-bosh
3. install vagrant-openstack dummy box
  # vagrant box add dummy https://github.com/cloudbau/vagrant-openstack-plugin/raw/master/dummy.box
3. ensure openstack credentials and parameters are provided as expected in the Vagrantfile
4. run
  # vagrant up --provider=openstack
