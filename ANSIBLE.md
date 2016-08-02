See official documentation, best practices here: http://docs.ansible.com/ansible/playbooks_best_practices.html

Ansible - create a playbook skeleton
------------------------------------

```shell
ansible-galaxy init [playbook-name] --force
```

Ansible - run command, script, playbook
---------------------------------------

```shell
ansible dev -i hosts -m command -a "uptime"
ansible dev -i hosts -m script -a test.sh -u vagrant
ansible-playbook -i hosts site.yml
```

Ansible - secret management with vault
--------------------------------------

```shell
ansible-vault encrypt group_vars/all/secrets/*
ansible-playbook -i hosts site.yml --ask-vault-pass
ansible-vault decrypt group_vars/all/secrets/*
```

Ansible - testing
-----------------

```shell
ansible-playbook -i hosts site.yml --check --diff
gem install serverspec
serverspec-init
rake spec
```
