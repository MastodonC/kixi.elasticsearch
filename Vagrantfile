# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure("2") do |config|

ENV['VAGRANT_DEFAULT_PROVIDER'] = 'docker'

  config.vm.provider "docker" do |d|

    d.build_dir	= "Docker"
    d.build_args=["-t",  "Elastic"]
    d.name="elastic_image"
    #Modify the line below! Change <file-path> to match your local file path.
    d.create_args=[ "-v", "<file-path>/kixi.elasticsearch/data-dir:/data"]
    d.cmd=["/elasticsearch/bin/elasticsearch", "-Des.config=/data/elasticsearch.yml"]

    config.vm.network :forwarded_port, host: 9200, guest: 9200
    config.vm.network :forwarded_port, host: 9300, guest: 9300
    
  end

end
