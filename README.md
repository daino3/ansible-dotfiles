## Ansible Playbook for Copying Dotfiles onto Dev/Test VM
I use thoughtbot's dotfiles for managing VIM, zsh, silver searcher, etc. This playbook copies my dotfiles to my VM. I've only run it against a CENTOS VM while paired with a vagrant file.

#### What It Does
+ installs EPEL, RCM, vim, git, silver searcher
+ Copies dotfiles into /home/vagrant
+ Copies any color schemes you've downloaded into /home/vagrant/.vim/colors
+ Sets an EDITOR, RCRC variable and sets /vagrant as root ssh directory
+ Installs Vundle & runs BundleInstall in vim

#### To Use
+ `git clone https://github.com/daino3/ansible-dotfiles.git`
+ add your addiotional configuration
+ In a project with Vagrant:

```ruby
# Vagrantfile
config.vm.define :test do |dev|
  dev.vm.provision :ansible do |ansible|
    ansible.playbook = '/Users/<YOUR-FILEPATH>/ansible-dotfiles/main.yml'
    ansible.groups = ansible_test_groups
  end
end
```
+ vagrant provision test

