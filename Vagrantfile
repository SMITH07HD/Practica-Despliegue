Vagrant.configure("2") do |config|
    # Configuración para la primera máquina virtual
    config.vm.define "webserver1" do |webserver1|
      webserver1.vm.box = "ubuntu/bionic64"  # Puedes cambiar la caja si prefieres otra distribución
      webserver1.vm.network "forwarded_port", guest: 80, host: 8081  # Redirige el puerto 80 del huésped al 8081 del anfitrión
      webserver1.vm.synced_folder "./html", "/var/www/html"  # Carpeta local a compartir con la VM
  
      webserver1.vm.provision "shell", inline: <<-SHELL
        sudo apt-get update
        sudo apt-get install -y apache2
        sudo systemctl start apache2
        sudo systemctl enable apache2
      SHELL
    end
  
    # Configuración para la segunda máquina virtual
    config.vm.define "webserver2" do |webserver2|
      webserver2.vm.box = "ubuntu/bionic64"  # Puedes cambiar la caja si prefieres otra distribución
      webserver2.vm.network "forwarded_port", guest: 80, host: 8082  # Redirige el puerto 80 del huésped al 8082 del anfitrión
      webserver2.vm.synced_folder "./html", "/var/www/html"  # Carpeta local a compartir con la VM
  
      webserver2.vm.provision "shell", inline: <<-SHELL
        sudo apt-get update
        sudo apt-get install -y apache2
        sudo systemctl start apache2
        sudo systemctl enable apache2
      SHELL
    end
  end