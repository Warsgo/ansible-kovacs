# TP Ansible

## Introduction

Ce dépôt contient les différents travaux pratiques réalisés autour de **Ansible**, un outil d’automatisation et de gestion de configuration.

Ansible permet d'automatiser des tâches comme :

- le déploiement de serveurs
- la configuration de machines
- l'installation de logiciels
- l'orchestration d'infrastructures

L'un des avantages principaux d'Ansible est qu'il fonctionne **sans agent** : il utilise simplement **SSH** pour communiquer avec les machines distantes. Les configurations sont décrites dans des fichiers appelés **playbooks**, écrits en **YAML**, ce qui les rend lisibles et faciles à maintenir.

Dans ce TP, nous allons suivre le cours disponible ici :  
https://formations.microlinux.fr/ansible/a-propos/

L'objectif est de découvrir progressivement :

- le fonctionnement d'Ansible
- la gestion d'inventaires
- l'exécution de commandes à distance
- l'utilisation de playbooks pour automatiser des tâches

---

## Sommaire

- [Atelier 1](./1-Atelier-1)
- [Authentification](./2-Authentification)
- [Direnv](./3-Direnv)
- [Configuration de Base](./4-Configuration-de-Base)
- [Idempotence](./5-Ansible-et-Idempotence)
- [Serveur Web Apache](./6-Serveur-Web-Apache)
- [Les Handlers](./7-Handlers)
- [Les Variables](./8-Variables)
- [Les Variables Enregistrées](./9-Variables-Enregistrées)
- [Facts et Variables Implicites](./10-Facts-et-Variables-Implicites)
- [Cibles Hétérogènes](./11-Cibles-Heterogenes)
- [Jinja & Templates](./12-Jinja-et-Templates)
---

## Structure du projet
```
.
├── README.md
└── Test_01-Test_02/
```

Chaque dossier correspond à une série de tests ou d'exercices réalisés pendant le TP.
