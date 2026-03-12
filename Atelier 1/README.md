# Installation d'Ansible sur Ubuntu

Étant donné qu'Ubuntu est basé sur Debian, le gestionnaire de paquets (`apt`) et les commandes associées sont exactement les mêmes que ceux utilisés pour la VM Debian dans votre cours.

## Résolution du Challenge n°1

### 1. Démarrez la VM Ubuntu depuis le répertoire `atelier-01`

```
vagrant up ubuntu
```

### 2. Connectez-vous à cette VM
```
vagrant ssh ubuntu
```
### 3. Rafraîchissez les informations sur les paquets
```
sudo apt update
```
### 4. Recherchez le paquet ansible avec les options appropriées
``` 
apt-cache search --names-only ansible
```
### 5. Installez le paquet officiel fourni par la distribution
```
sudo apt install -y ansible
```
### 6. Vérifiez si l'installation s'est bien déroulée (et notez la version)
```
ansible --version
```
### 7. Déconnectez-vous et supprimez la VM
```
exit
vagrant destroy -f ubuntu
```
