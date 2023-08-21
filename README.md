# transistor-build

Previously, any VM I would build would have a [long shell script](https://github.com/An00bRektn/ignition-key) to install things. It was simple, but definitely annoying to debug and was hard if installation instructions changed.

[Ansible Playbooks](https://www.ansible.com/), while maybe a bit overkill for a single host, is, in many ways, much easier to maintain and also incrementally makes changes. (this was also mostly an opportunity for me to learn how to use ansible)

I have cut a few things out from the actual playbook I maintain because I don't want to accidentally give away stuff I don't mean to, but the playbook is mostly the same. **This is designed to run on Kali Linux** so don't expect it to work on any old host. 

## Usage
```
pip3 install ansible
export PATH=$PATH:/home/kali/.local/bin
ansible-galaxy install -r requirements.yml
sudo whoami
ansible-playbook main.yml
```

> [!WARNING] 
> As of writing (8-20-23), the vscode galaxy is a bit buggy, but I don't want to write my own role. This [pull request](https://github.com/gantsign/ansible-role-visual-studio-code/pull/244) covers the appropriate changes that need to be made, and just reboot after installing for it to work properly.

## Additional Notes
- Although I like [Sliver](https://github.com/BishopFox/sliver), I kept out of the ansible build because I'd rather run that outside of the context of the playbook
- Don't have a great way to transfer files from one machine to another, will set that up some other time
- Need to change Kali password, that is something for you to do outside of the playbook
- It doesn't actually install pwndbg, mainly because I always forget if you're supposed to run `setup.sh` as a user or root, and I didn't feel like testing it

## References
- [ippsec/parrot-build](https://github.com/IppSec/parrot-build)
- [waylonwalker](https://waylonwalker.com/install-rust/)
- [mttaggart/seclab](https://github.com/mttaggart/seclab)