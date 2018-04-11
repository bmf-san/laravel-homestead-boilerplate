# Laravel Homestead Boilerplate
This is a boilerplate for laravel working for homestead.

# Requirements
- composer
- vagrant
- virtualbox
- ssh key

# Get Started
## Setup for Laravel
`composer create-project "laravel/laravel=5.2.*" projectname`
※You don't need execute this command if you use this boilerplate repository.

`cd app`
`composer install`

## Setup for Homestead
### Install the vagrant box.
`vagrant box add laravel/homestead`

### Install the homestead repository
`cd ~`
`git clone https://github.com/laravel/homestead.git Homestead`
`bash init.sh`

`vi Homestead.yaml`

Then, edit it like this.

```:bash
ip: "192.167.10.99" // edit
memory: 2048
cpus: 1
provider: virtualbox

authorize: ~/.ssh/id_rsa.pub

keys:
    - ~/.ssh/id_rsa

folders:
    - map: ~/localdev/project/laravel // edit
      to: /home/vagrant/code

sites:
    - map: laravel // edit
      to: /home/vagrant/code/public

databases:
    - homestead

# blackfire:
#     - id: foo
#       token: bar
#       client-id: foo
#       client-token: bar

# ports:
#     - send: 50000
#       to: 5000
#     - send: 7777
#       to: 777
#       protocol: udp
```

And, edit a hosts file.

`vi /etc/hosts`

```
##
# Host Database
#
# localhost is used to configure the loopback interface
# when the system is booting.  Do not change this entry.
##
127.0.0.1       localhost
255.255.255.255 broadcasthost
::1     localhost
192.167.10.99  laravel // edit
192.167.10.99  homestead  # VAGRANT: e78b975204ccde53ef11f1ffe284d4f4 (homestead-7) / b212bb82-8dc8-405b-8507-fa284ddb9aa8
```

## Start up the vagrant
`cd ~/Homestead`
`vagrant up`

Then you will be able to access the site via your web browser.
`http://laravel`
