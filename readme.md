# [AS211184](https://bgp.he.net/AS211184) Playbooks

This is my ansible project to manage my own infrastructure for my personal AS for labbing and selfhost requirements. These exist because I like this.

## Structure

## Running a playbook
``eval `ssh-agent` ``   
`ssh-add <ssh-key here>`      
`ansible-playbook -i inventories/development <playbook>.yaml` (vault pass is asked by default so --ask-vault-pass is not needed)

## Encrypting passwords
`ansible-vault encrypt_string`    
type in your ansible vault password (I use the same generated vault key for all my variables in this project and store the one password in my password manager.)
Next enter your variable to encrypt and press ctrl+d twice.

## Playbooks
### Setup
- Only run once otherwise the root password will be changes multiple times
- Setup a clean debian host from scratch. Make sure a user exists and the root password is known, the run should be done with: `-u debian -k --ask-become-pass`

### Common
- Initial run can be done with `-u debian -k --ask-become-pass`, subsequent runs can be done with the configured `default_user` and an ssh key
- Updates packages to latest version
- Set default user and removes the setup one (debian or similar)
- Installs packages needed for daily operation and network debugging

## Todo
- frr
- iptables
