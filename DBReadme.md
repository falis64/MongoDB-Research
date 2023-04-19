#

- add new line to vagrant file ```config.vm.define "app" do |app|``

- changed all the config commands to app instead of app - so that we can give instructions to just app

- make sure all the lines below the new one are indented under the new config line so that it knows it relates to the vm (first line)

should look like:
```
Vagrant.configure("2") do |config|

  config.vm.define "app" do |app|
   app.vm.box = "ubuntu/xenial64"
   app.vm.network "private_network", ip: "192.168.20.100"
   app.vm.provision "shell", path: "provision.sh"
   app.vm.synced_folder "app", "/home/vagrant/app"
  end
  

  config.vm.define "db" do |db|
    db.vm.box = "ubuntu/xenial64"
    db.vm.network "private_network", ip: "192.168.20.150"
  end

end
```

if you run vagrant up, you should see that it recognises both configs. You'll also be able to see this on the virtual box:


