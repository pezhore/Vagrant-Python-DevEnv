# Vagrant-Python-DevEnv

## Overview

Vagrant config for Ubuntu 17.04 Pthon3 development environment. Pulls down a minimal Ubuntu 17.04 server image, installs/configures via ansible playbook. Also includes a packer build template that can be used for future upgrades/builds.

## Post Provision Actions

The `vagrant up` command will attempt to use ansible for post provisioning to do the following:

* Get aptitude for upgrade
* Safe system upgrade via aptitude
* Add vim apt-repo `ppa:pi-rho/dev` - this is used to get a python capable vim package.
* Install Packages via apt:
  * git
  * python3.6
  * python-dev
  * python3-dev
  * python3.6-dev
  * python3.6-venv
  * build-essential
  * python3-pip
  * tmux
  * vim
  * cmake
  * python-software-properties
  * software-properties-common
  * vim-gtk
* Alias pip3 to pip
* Install global python requirements:
  * virtualenv
  * virtualenvwrapper
  * flake8
* Pulldown tmux config from [gist](https://gist.githubusercontent.com/pezhore/23a8fa5174f59c7b56d70ff7cf02c372/raw/.tmux.conf)
* Pulldown vim config from [gist](https://gist.githubusercontent.com/pezhore/9e4a1333ac82a8bf41d9d529a3c4a88f/raw/.vimrc)
* Pulldown bash\_aliases from [gist](https://gist.githubusercontent.com/pezhore/8f2bb97cecd2bc18e987a9fcafc6de33/raw/.bash_aliases)
* Pulldown bashrc from [gist](https://gist.githubusercontent.com/pezhore/795d66c0cc628d184fc43c9f9889b8d3/raw/.bashrc)
* Create VIM Autoload folder
* Create vim bundle folder
* Install Vundle
* Install Git bash completion
* Install VIM plugins
* Compile [YouCompleteMe](http://valloric.github.io/YouCompleteMe/)
