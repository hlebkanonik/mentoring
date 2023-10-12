### Exercise 1: Installing Vagrant
**Objective**: Install Vagrant on your local machine.

**Steps**:
1. Go to the [Vagrant website](https://www.vagrantup.com/).
2. Download and install Vagrant for your operating system (Windows, macOS, or Linux).
3. Verify the installation by opening a terminal/command prompt and running `vagrant --version`.

### Exercise 2: Creating a Vagrantfile
**Objective**: Create a Vagrantfile to define a VM with Ubuntu and Docker.

**Steps**:
1. Create a new directory for your Vagrant project.
2. Inside this directory, create a file named `Vagrantfile` (no file extension).
3. Edit the `Vagrantfile` to define a VM using an Ubuntu box with Docker.

```ruby
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/focal64"
  
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
  end

  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y docker.io
    sudo usermod -aG docker vagrant
    sudo systemctl enable docker
  SHELL
end
```

4. Save the `Vagrantfile`.

### Exercise 3: Launching the VM with Docker
**Objective**: Start the VM and verify Docker is installed.

**Steps**:
1. Open a terminal/command prompt and navigate to the directory containing the `Vagrantfile`.
2. Run `vagrant up` to start the VM.
3. Once the VM is up and running, SSH into it using `vagrant ssh`.
4. In the VM, run `docker --version` to verify that Docker is installed.

### Exercise 4: Creating Multiple VMs
**Objective**: Define a multi-VM environment with Vagrant.

**Steps**:
1. Extend your existing `Vagrantfile` to define two VMs.
2. Customize each VM with different configurations (e.g., memory, CPU, etc.).
3. Modify the provision script to install Docker on both VMs.

```ruby
Vagrant.configure("2") do |config|
  config.vm.define "vm1" do |node|
    node.vm.box = "ubuntu/focal64"
    node.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
    end
    node.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y docker.io
      sudo usermod -aG docker vagrant
      sudo systemctl enable docker
    SHELL
  end

  config.vm.define "vm2" do |node|
    node.vm.box = "ubuntu/focal64"
    node.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
    end
    node.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y docker.io
      sudo usermod -aG docker vagrant
      sudo systemctl enable docker
    SHELL
  end
end
```

### Exercise 5: Managing VMs with Vagrant
**Objective**: Practice Vagrant commands for managing VMs.

**Steps**:
1. Use `vagrant up` to start both VMs.
2. Use `vagrant status` to check the status of your VMs.
3. Use `vagrant ssh [vm-name]` to SSH into a specific VM (replace `[vm-name]` with the actual name).
4. Use `vagrant halt [vm-name]` to shut down a specific VM.
5. Use `vagrant destroy [vm-name]` to remove a specific VM.

Remember to replace `[vm-name]` with the actual name you gave to your VMs.

These exercises should provide you with a solid foundation for working with Vagrant, Docker, and VirtualBox. Have fun exploring and experimenting!
