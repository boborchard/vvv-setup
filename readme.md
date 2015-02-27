# Local Development Environment Configuration

For use in onboarding new developers or staff members for a local development environment. Keep in mind that:

  - Our local development environments are set to ~/sites/Vagrant
  - All sites (WordPress) are managed with VVV
  - We'll install a dashboard for seeing all local sites

### Installing Virtualbox
1. Download [VirtualBox]
2. Double click the .dmg and follow the on-screen instructions

### Installing iTerm
1. Download [iTerm]
2. Unpack the .zip folder and drag iTerm.app to your Applications directory

### Installing Vagrant
1. Download [Vagrant]
2. Double click the Vagrant.pkg file and follow the on-screen instructions

### Installing VVV (Varying Vagrant Vagrants)
This is where things start to get fun. Let's set up the prerequisites for VVV by running the following command:

    $ vagrant plugin install vagrant-hostsupdater && vagrant plugin install vagrant-triggers

Run the following to create your local Vagrant folder and download VVV into that directory:

    $ cd ~/sites/ && git clone git://github.com/Varying-Vagrant-Vagrants/VVV.git Vagrant
    
Let's set up your bash profile to recognize shorthand for running Vagrant Up and Vagrant Halt:

    $ nano ~/.bash_profile
    
Add the following to the file and hit CTRL+X to close, Y to save and overwrite the bash file:

    alias vup="cd ~/sites/Vagrant && vagrant up"
    alias vdown="cd ~/sites/Vagrant && vagrant halt"

Don't forget to refresh your bash profile:

    source ~/.bash_profile
    
Once this is completed, let's run *vup* to start up and provision your development environment.

## Installing VVV Site Wizard

    $ brew install tinypint/vv/vv

Information on the VV Site Wizard forked from Brad Parbs (https://github.com/bradp/vv) is available at https://github.com/tinypint/vv. This is kept up to date for our internal use but we'll submit pull requests as necessary.

### Installing the VVV Dashboard

Our VVV Dashboard is based off the VVV Dashboard by Leo Gopal (https://github.com/leogopal/VVV-Dashboard). To install it, run the following:

    $ cd ~/Sites/Vagrant/www/default
    $ git clone git@github.com:tinypint/VVV-Dashboard.git VVV-Dash-Files-tmp
    $ sudo ditto VVV-Dash-Files-tmp/dashboard dashboard/
    $ sudo ditto VVV-Dash-Files-tmp/dashboard-custom.php dashboard-custom.php
    $ sudo rm -rf VVV-Dash-Files-tmp
    
This will install the dashboard which will be available at http://vvv.dev/dashboard/index.php

[VirtualBox]:http://download.virtualbox.org/virtualbox/4.3.22/VirtualBox-4.3.22-98236-OSX.dmg
[iTerm]: https://iterm2.com/downloads/stable/iTerm2_v2_0.zip
[Vagrant]: https://dl.bintray.com/mitchellh/vagrant/vagrant_1.7.2.dmg