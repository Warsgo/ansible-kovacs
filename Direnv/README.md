## Gestion des variables de projet avec Direnv

L'objectif de ce quatrième atelier a été de prendre en main `direnv`, un utilitaire externe à Ansible mais particulièrement utile pour l'organisation des configurations. Cet outil permet de charger et décharger dynamiquement des variables d'environnement en fonction du répertoire de travail courant.

### 1. Initialisation de l'environnement
Le répertoire de travail a été défini sur `atelier-04`, contenant les configurations pour deux machines virtuelles : une sous Debian et une sous Rocky Linux. Les deux instances ont été démarrées simultanément :

```
cd ~/formation-ansible/atelier-04
vagrant up
```
### 2. Déploiement et tests sous Debian

Une connexion SSH a d'abord été établie sur la machine Debian :
```
vagrant ssh debian
```
#### Installation et configuration

Les informations sur les paquets ont été mises à jour, puis direnv a été installé depuis les dépôts officiels. Pour que l'outil s'intègre au shell Bash, une directive a été ajoutée au fichier de configuration de l'utilisateur, suivie d'un rechargement du profil :
```
sudo apt update
sudo apt install -y direnv
echo 'eval "$(direnv hook bash)"' >> ~/.bashrc
source ~/.bashrc
```
#### Validation du fonctionnement

Un répertoire de test nommé monprojet a été créé. À l'intérieur, un fichier .envrc a été généré pour définir une variable d'environnement nommée TESTVAR :
```
mkdir -v monprojet
cd monprojet/
echo "export TESTVAR=Yatahongaga" > .envrc
```
Pour des raisons de sécurité, direnv bloque l'exécution des nouveaux fichiers .envrc par défaut. Une autorisation explicite a donc été requise :
```
direnv allow
```
Le comportement dynamique a été vérifié : la variable TESTVAR était bien définie à l'intérieur du répertoire monprojet, et automatiquement déchargée en le quittant.
#### Définition de chemins absolus

Le fichier .envrc a ensuite été modifié pour exploiter la fonction expand_path, très utile pour les futurs projets Ansible. Cette fonction permet de transformer un chemin relatif en chemin absolu. La variable ANSIBLE_CONFIG a été configurée de cette manière :
```
echo 'export ANSIBLE_CONFIG=$(expand_path ansible.cfg)' > .envrc
direnv allow
```
La valeur de ANSIBLE_CONFIG correspondait bien au chemin absolu du fichier ansible.cfg (ex: /home/vagrant/monprojet/ansible.cfg), et cette variable restait accessible même en naviguant dans un sous-répertoire du projet.

La session Debian a ensuite été clôturée :
```
exit
```
### 3. Déploiement et tests sous Rocky Linux

Une connexion SSH a ensuite été ouverte sur la machine Rocky Linux :
```
vagrant ssh rocky
```
#### Installation manuelle

Contrairement à Debian, Rocky Linux ne propose pas direnv dans ses dépôts officiels ni dans les dépôts tiers (EPEL). L'installation a donc été réalisée manuellement en téléchargeant le binaire précompilé depuis les sources officielles du projet sur GitHub, avant de lui attribuer les droits d'exécution et de configurer le shell :
```
VER="2.37.1"
sudo wget [https://github.com/direnv/direnv/releases/download/v$VER/direnv.linux-amd64](https://github.com/direnv/direnv/releases/download/v$VER/direnv.linux-amd64) -O /usr/local/bin/direnv
sudo chmod 0755 /usr/local/bin/direnv
echo 'eval "$(direnv hook bash)"' >> ~/.bashrc
source ~/.bashrc
```
#### Validation

La procédure de test a été reproduite pour valider l'installation manuelle. Un répertoire test a été créé, une variable d'environnement y a été déclarée via .envrc, et l'autorisation a été accordée :
```
mkdir test
cd test/
echo "export TESTVAR=Yatahongaga" > .envrc
direnv allow
```
Le test a confirmé que la variable se chargeait et se déchargeait correctement en entrant et en sortant du répertoire.

La session Rocky Linux a été clôturée :
```
exit
```
### 4. Nettoyage de l'infrastructure

L'atelier s'est conclu par la destruction des deux machines virtuelles pour restaurer l'état initial du système hôte :
```
vagrant destroy -f
```
