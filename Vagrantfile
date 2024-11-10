# Vagrantfile para configurar una VM con Apache y un directorio compartido
Vagrant.configure("2") do |config|
    # Usar imagen base de Ubuntu
    config.vm.box = "ubuntu/bionic64"
    
    # Configurar VM con 512 MB de RAM y 1 CPU
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 1
    end
    
    # Configurar red para acceder a Apache en localhost:8080
    config.vm.network "forwarded_port", guest: 80, host: 8080
    
    # Directorio compartido entre la VM y el sistema local
    config.vm.synced_folder "./paginas", "/var/www/html", type: "virtualbox"
    
    # Provisionamiento para instalar Apache
    config.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y apache2
      sudo systemctl enable apache2
      sudo systemctl start apache2
    SHELL
  end
  