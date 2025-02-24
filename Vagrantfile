Vagrant.configure("2") do |config|
  config.vm.box = "debian/bookworm64"

  # Port Forwarding 
  config.vm.network "forwarded_port", guest: 5000, host: 1234

  # Provisioning
  config.vm.provision "shell", inline: <<-SHELL
      sudo apt update
      sudo apt install -y python3 python3-venv python3-pip git nano vim curl

      # Setup Flask App
      cd /home/vagrant
      python3 -m venv flask_venv
      source flask_venv/bin/activate
      pip install Flask
  SHELL

  # Upload hello.py to VM
  config.vm.provision "file", source: "hello.py", destination: "/home/vagrant/hello.py"

  # Start Flask on boot
  config.vm.provision "shell", inline: <<-SHELL
      cd /home/vagrant
      source flask_venv/bin/activate
      nohup flask --app hello run --host=0.0.0.0 & 
  SHELL
end