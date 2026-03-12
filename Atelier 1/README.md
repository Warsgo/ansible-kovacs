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


## Résolution du Challenge n°1
