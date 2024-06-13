# -*- mode: ruby -*-
# vi: set ft=ruby :
$script = <<-SCRIPT

packages=("git" "docker.io" "mysql-server" "httpd" "terraform")
#loop through each package and install it, update, upgrade and install it
for package in "${packages[@]}"
do 
    echo "installing $package..."
    apt install --only-upgrade -y "$package"
    apt install -y httpd mariadb-server
    wget -O- https://apt.releases.hashicorp.com/gpg | gpg --dearmor | sudo tee /usr/share/keyrings/hashicorp-archive-keyring.gpg
    echo "updating and upgrading $package..."
    apt-get update
    apt-get upgrade -y
    systemctl start
    systemctl enable
done

SCRIPT
