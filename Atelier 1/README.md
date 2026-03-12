# Installation d'Ansible sur Ubuntu

Étant donné qu'Ubuntu est basé sur Debian, le gestionnaire de paquets (`apt`) et les commandes associées sont exactement les mêmes que ceux utilisés pour la VM Debian.

## Résolution du Challenge n°1

### 1. Démarrer la VM Ubuntu depuis le répertoire `atelier-01`

```
vagrant up ubuntu
```

### 2. Ce connecter à cette VM
```
vagrant ssh ubuntu
```
### 3. Rafraîchisser les informations sur les paquets
```
sudo apt update
```
### 4. Rechercher le paquet ansible avec les options appropriées
``` 
apt-cache search --names-only ansible
```
### 5. Installer le paquet officiel fourni par la distribution
```
sudo apt install -y ansible
```
### 6. Vérifier si l'installation s'est bien déroulée (et notez la version)
```
ansible --version
```

![Version Ansible](Atelier1-Challenge1.png)
### 7. Ce Déconnecter et supprimez la VM
```
exit
vagrant destroy -f ubuntu
```
---


## Résolution du Challenge n°2

Ce second exercice a consisté à répéter le déploiement en intégrant cette fois-ci un dépôt PPA, dans le but d'observer les différences de gestion de paquets.
### 1. Initialisation et connexion

Une nouvelle instance de la machine virtuelle Ubuntu a été montée et accédée en SSH :
```
vagrant up ubuntu
vagrant ssh ubuntu
```
#### 2. Ajout du dépôt tiers et installation

Le dépôt PPA officiel maintenu par le projet Ansible a été ajouté aux sources du système. Après une mise à jour de la liste des paquets, Ansible a été installé :
Bash
```
sudo apt-add-repository ppa:ansible/ansible
sudo apt update
sudo apt install -y ansible
```
### 3. Vérification et comparaison des versions

La version issue du dépôt PPA a été affichée pour être comparée à la précédente :
```
ansible --version
```
![Version Ansible](Atelier1-Challenge2.png)

L'observation a montré que la version d'Ansible fournie par le dépôt PPA est plus récente que celle installée lors du Challenge 1. Cette différence s'explique par le fait que les dépôts officiels d'Ubuntu figent les versions pour garantir la stabilité globale du système, tandis que le dépôt PPA est directement mis à jour par les développeurs d'Ansible avec les dernières versions stables.

### 4. Suppression de l'environnement

Comme pour l'exercice précédent, la session a été fermée et l'instance Vagrant a été détruite pour libérer les ressources :
```
exit
vagrant destroy -f ubuntu
```

---


## Résolution du Challenge n°3
