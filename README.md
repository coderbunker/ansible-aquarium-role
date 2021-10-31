Aquarium
=========

Ce rôle sert à déployer/remettre en état un serveur L'Aquarium + Jitsi Meet via Docker Compose.

Requirements
------------

### Matériel
* 4 vcore + 8 Go de RAM + BEAUCOUP de bande passante

### Système d'exploitation
* Ubuntu 20.04 (seul SE testé)

### Docker et Docker Compose
* IMPORTANT : Docker et Docker Compose NE SONT PAS installés par le rôle
* NOTE : Les paquets .deb disponibles dans Ubuntu 20.04 (universe) sont suffisants

Role Variables
--------------

### defaults/main.yml

Dependencies
------------

Aucune dépendance à d'autres rôles Ansible.

Example Playbook
----------------

```
- name: "Deployer un serveur L'Aquarium + Jitsi Meet via Docker Compose"
  hosts: 
    - all
  vars:
    # Supplanter ici les variables du role 'aquarium' au besoin
    utilisateur_unix: "jitsi442"
    fuseau_horaire: "UTC-5"
    aquarium_domaine: "unvraidomaine.org"
    jitsi_domaine: "jitsi.unvraidomaine.org"
    letsencrypt_courriel: "un_nom@jitsi.unvraidomaine.org"

  pre_tasks:
    - name: "Installer Docker et Docker Compose"
      apt:
        name: docker.io, docker-compose
        state: present
      become: yes
  roles:
    - ansible-aquarium-role
```

License
-------

GPL-3.0-only

Author Information
------------------

Mathieu GP, admin. sys. pour Coderbunker
