# Macsible

[![Build Status](https://travis-ci.org/macsible/macsible.svg?branch=master)](https://travis-ci.org/macsible/macsible)


### Requirements

Ensure the following requirements are already installed and working:

- macOS 10.11 (El Capitan)
- Command Line Developer Tools

See [here](docs/install_requirements.md) for assistance.


## Installation & usage

*NOTE: All commands listed on this page are to be run from the same location as this README.md file.*


### Install dependencies

A script is included to ensure certain dependencies are met:

- Install Homebrew (if not already installed)
- Install separate Python (via Homebrew if not already installed)
- Install Ansible (via Homebrew if not already installed)
- Create required files if not present: config.yml, config.local.yml, mac.yml, requirements.yml
- Download required Ansible Galaxy roles

To execute this script run:

```
bash init.sh
```


### Configure

Default variables can be overridden in config.yml.

config.local.yml can be used to override config.yml which can be useful when you need to use different values for just a few variables on a specific system. By default config.local.yml is ignored by git.


### Updating externally sourced roles

If you decide to add/edit the roles listed in requirements.yml (highly encouraged!) then you'll need to make sure that those dependencies are in place before running your playbook:

```
ansible-galaxy install -r requirements.yml --force
```


### Run the Ansible playbook

The primary Ansible playbook file is called mac.yml and can be run using the following command (asks for sudo password):

```
ansible-playbook mac.yml -K
```

To run only certain tags (e.g. `firefox` and `flux`):

```
ansible-playbook mac.yml -K -t "firefox,flux"
```
