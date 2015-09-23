# -*- mode: ruby -*-
# vi: set ft=ruby :

VENDOR_ID = "0xdead"  # Vendor & Product IDs of the USB to TTL device used for flashing.
PRODUCT_ID = "0xbeef"

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty32"

  config.vm.provider :virtualbox do |vb|
    vb.customize ['modifyvm', :id, "--usb", "on"]
    vb.customize ['usbfilter', 'add', '0',
                  '--target', :id,
                  '--name', 'USBtoTTL',
                  '--vendorid', VENDOR_ID,
                  '--productid', PRODUCT_ID]
  end

  config.vm.provision :ansible do |ansible|
    ansible.playbook = "playbook.yml"
  end
end
