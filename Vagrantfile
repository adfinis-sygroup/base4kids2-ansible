Vagrant.configure("2") do |config|
  config.vm.synced_folder "~/.base4kids", "/home/vagrant/.base4kids"
  config.vm.box = "adsy-centos-7.4.1708.box"
  config.vm.box_download_checksum_type = "sha256"
  config.vm.box_url = "https://vagrant.adfinis-sygroup.ch/libvirt-adsy-centos-7.4.1708.box"
  config.vm.box_download_checksum = "2fd097441ebd81329482b6cfabfd841d926d51643ad873f6a762aee31d63a8e4"

  config.ssh.insert_key = false

  # # # # # #
  # GALERA
  # # # # # #
  config.vm.define "galera-01" do |g|
    g.vm.network "private_network", ip: "192.168.56.3"
  end
  config.vm.define "galera-02" do |g|
    g.vm.network "private_network", ip: "192.168.56.4"
  end
  config.vm.define "galera-03" do |g|
    g.vm.network "private_network", ip: "192.168.56.5"
  end

  # # # # # #
  # PROXYSQL
  # # # # # #
  config.vm.define "proxysql-01" do |g|
    # eth0
    g.vm.network "private_network", ip: "192.168.56.10"
    # keepalived interface (eth1)
    g.vm.network "private_network", type: "dhcp"
  end
  config.vm.define "proxysql-02" do |g|
    # eth0
    g.vm.network "private_network", ip: "192.168.56.11"
    # keepalived interface (eth1)
    g.vm.network "private_network", type: "dhcp"
  end

  # # # # # #
  # HAPROXY
  # # # # # #
  config.vm.define "haproxy-01" do |g|
    # eth0
    g.vm.network "private_network", ip: "192.168.56.61"
    # keepalived interface (eth1)
    g.vm.network "private_network", type: "dhcp"
  end
  config.vm.define "haproxy-02" do |g|
    # eth0
    g.vm.network "private_network", ip: "192.168.56.62"
    # keepalived interface (eth1)
    g.vm.network "private_network", type: "dhcp"
  end

  # # # # # #
  # COLLABORA
  # # # # # #
  config.vm.define "collabora-01" do |g|
    g.vm.network "private_network", ip: "192.168.56.51"
  end
  config.vm.define "collabora-02" do |g|
    g.vm.network "private_network", ip: "192.168.56.52"
  end

  # # # # # #
  # NEXTCLOUD
  # # # # # #
  config.vm.define "nextcloud-01" do |g|
    g.vm.synced_folder "/tmp/ncshare", "/srv/nextcloud_data", type: "nfs", nfs_udp: false
    g.vm.network "private_network", ip: "192.168.56.41"
    # db interface (eth1)
    g.vm.network "private_network", type: "dhcp"
  end
  config.vm.define "nextcloud-02" do |g|
    g.vm.synced_folder "/tmp/ncshare", "/srv/nextcloud_data", type: "nfs", nfs_udp: false
    g.vm.network "private_network", ip: "192.168.56.42"
    # db interface (eth1)
    g.vm.network "private_network", type: "dhcp"
  end

  # # # # # #
  # REDIS
  # # # # # #
  config.vm.define "redis-master-01" do |g|
    g.vm.network "private_network", ip: "192.168.56.31"
  end
  config.vm.define "redis-slave-01" do |g|
    g.vm.network "private_network", ip: "192.168.56.32"
  end

  config.vm.provider :virtualbox do |vb|
        vb.memory = 512
        vb.cpus = 1
  end
end
