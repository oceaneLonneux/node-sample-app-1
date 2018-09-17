Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"
  config.vm.network("private_network", ip: "192.168.10.100")
  config.hostsupdater.aliases = ["development.local"]
end

required_plugins = ['vagrant-hostmanager']
required_plugins.each do |plugin|
  exec "vagrant plugin install #{plugin}" unless Vagrant.has_plugin? plugin
end
# .has_plugin? is a method
