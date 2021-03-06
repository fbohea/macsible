# Macsible

[![Build Status](https://travis-ci.org/macsible/macsible.svg?branch=master)](https://travis-ci.org/macsible/macsible)


### Requirements

Ensure the following requirements are already installed and working on your local system:

- [macOS](https://support.apple.com/en-us/HT201372) 10.10, 10.11 or 10.12
- Command Line Developer Tools

See [here](docs/install_requirements.md) for assistance.


## Forking and customisation

1. Fork the repository at [https://github.com/macsible/macsible](https://github.com/macsible/macsible).
2. Clone the fork to your local system (this is now the repository you will use to store your own customisations).
3. Navigate to the local clone using your terminal app of choice.
4. Follow the usage instructions below.
5. Commit and push any customisations to your local clone back upstream to your fork.

You can see a working example of a forked and customised repository at [https://github.com/danbohea/macsible](https://github.com/danbohea/macsible)

## Usage

*NOTE: All commands below are to be run from the root of this codebase.*


### Install dependencies

A script is included to ensure certain dependencies are met:

- Install pip (if not already installed)
- Install Ansible (if not already installed)
- Create required files if not present: config.yml, config.local.yml, mac-custom.yml, requirements.yml
- Download required Ansible Galaxy roles

To execute this script run:

```
bash init.sh
```


### Configure

Default variables can be overridden in config.yml.

config.local.yml can be used to override config.yml which can be useful when you need to use different values for just a few variables on a specific system. By default config.local.yml is ignored by git.


### Updating externally sourced roles

If you decide to add/edit the roles listed in requirements.yml (highly encouraged!) then you'll need to make sure that those dependencies are in place before running your playbook. After editing requirements.yml you'll want to run the following command before running your playbook:

```
ansible-galaxy install -r requirements.yml --force
```


### Run the Ansible playbook

The primary Ansible playbook file is called macsible.yml and can be run using the following command (asks for sudo password):

```
ansible-playbook macsible.yml -K
```

To run only certain tags (e.g. `firefox` and `flux`):

```
ansible-playbook macsible.yml -K -t "firefox,flux"
```
