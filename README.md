# challenge-s08-e01

## Création de votre première arbo Ansible :

Placer dans ce dépôt une arborescence ansible :
- un répertoire etc/ avec dedans le fichier hosts qui contient votre inventaire, ex :
```
student@profy12-server:~/ansible-old$ cat etc/hosts 
ansible-test ansible_host=10.51.164.77
testreseau ansible_host=10.51.164.154
third ansible_host=10.252.235.79
```

- un répertoire playbooks/ qui contient dedans une ou des recettes, ex :
```
student@profy12-server:~/ansible-old$ cat playbooks/recette.yml 
---
- name: toto.txt
  hosts: ansible-test
  remote_user: root

  tasks:
  - name: create empty toto.txt file
    ansible.builtin.file:
      path: /etc/toto.txt
      state: touch

  - name: install needed packages
    ansible.builtin.apt:
      name: cowsay
      state: present
      update_cache: yes

  - name: run a specific command
    ansible.builtin.shell:
      cmd: cowsay "hello DevOps"
```

## Déployez l'arbo

En utilisant un workflow Github Action associé à ce dépôt et un runner local déployé sur votre VM serveur, déployez l'arborescence dans le répertoire utilisateur student de votre vm cloud serveur.
