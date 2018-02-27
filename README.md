## DrupalVM | Ubuntu 16.04 & Drupal 7 instance
Based on: https://github.com/geerlingguy/drupal-vm

### Current Environment:
Mac OS X El Capitan 10.12.6
Python 2.7.14

### Dependencies
* Vagrant
* VirtualBox
* Ansible 2.2 or greater

* VirtualBox Plug-in:  
`$ vagrant plugin install vagrant-vbguest`

Check Python from Terminal  
`$ python --version`

Open terminal and clone the DrupalVM repository to the 'desktop'  
`$ cd Desktop`  
`$ git clone https://github.com/geerlingguy/drupal-vm.git`

#### Open drupalvm in terminal  
Change repository folder name to "drupalvm"  
`$ mv drupal-vm drupalvm`

Create a Drupal folder  
`$ cd drupalvm`  
`$ mkdir "drupal"`

Open drupalvm in atom  
`$ atom open`

##### Duplicate the following and rename as suggested
* default.config.yml => config.yml
* example.drupal.make.yml => drupal.make.yml

##### config.yml:
Set to the following:
* drupal_build_makefile: true
* drupal_build_composer: false
* drupal_build_composer_project: false
* drupal_core_path: "/var/www/drupalvm/drupal"
* drupal_major_version: 7
* php_version: "5.6"

##### main.yml
provisioning/roles/geerlingguy.drush/defaults/main.yml  

Set the following as suggested:
* drush_launcher_install: no
* drush_install_from_source: yes
* drush_source_install_version: "8.1.15"

##### drupal.make.yml
Make sure the these are set to the following Inside drupal.make.yml
* core: "7.x"
* version: "7.54"

Open the drupalvm folder in terminal  
`$ vagrant up`

Open terminal and configure host machine to access the VM  
`$ nano ~/.bash_profile`

* To the bottom of the file add: 192.168.88.88
* Save and Exit: CTRL + X
* To save the changes enter: Yes

Reload Terminal bash profile settings  
`$ source ~/.bash_profile`

Adjust permissions to drupalvm/drupal folder
* navigate to drupalvm/drupal
* right click -> select get info
* adjust staff permissions to Read & Write
* click the gear at the bottom
* select: Apply to enclosed items

##### Upon successful build  
General VM Information:  
http://dashboard.drupalvm.test  
http://192.168.88.88
Local Drupal Website: drupalvm.test  
Drupal username: admin  
Drupal password: admin  
SQL username: root  
SQL password: root
