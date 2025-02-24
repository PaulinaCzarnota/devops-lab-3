Vagrant.configure("2") do |config|
  config.vm.box = "debian/bookworm64"

  # Port Forwarding
  config.vm.network "forwarded_port", guest: 5000, host: 8081

  # Provisioning
  config.vm.provision "shell", inline: <<-SHELL
      sudo apt update
      sudo apt install -y python3 python3-venv python3-pip git nano vim curl

      # Setup Flask App
      cd /home/vagrant
      python3 -m venv flask_venv
      source flask_venv/bin/activate
      pip install Flask

      # Create Flask Web App (if it doesn’t exist)
      if [ ! -f hello.py ]; then
          echo "from flask import Flask" > hello.py
          echo "app = Flask(__name__)" >> hello.py
          echo "@app.route('/')" >> hello.py
          echo "def hello():" >> hello.py
          echo "    return '<p>Hello, World!</p>'" >> hello.py
          echo "@app.route('/about')" >> hello.py
          echo "def about():" >> hello.py
          echo "    return '<p>This is a Flask web app running in a Linux VM.</p>'" >> hello.py
      fi

      # Run Flask on Boot
      nohup flask --app hello run --host=0.0.0.0 &
  SHELL
end