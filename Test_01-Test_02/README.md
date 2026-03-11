# Compte-rendu du TP : Déploiement d'un Laboratoire Ansible avec Vagrant

Voici un résumé concis des manipulations effectuées lors de ce TP, axé sur la mise en place de l'environnement et les deux phases de test.

##  Préparation du Lab (Le contexte)

Mise en place d'un environnement de travail isolé (Linux Mint sur un SSD externe) pour protéger le système principal. L'environnement a été configuré avec les outils d'infrastructure as code :
* **VirtualBox** : Hyperviseur pour exécuter les machines virtuelles (VM).
* **Vagrant** : Orchestrateur pour automatiser le déploiement des VM.
* **GAnsible** : Outils pour configurer l'infrastructure.

---

##  Test 01 : Validation du fonctionnement de base

L'objectif était de s'assurer que la chaîne logicielle (Vagrant + VirtualBox) communiquait parfaitement en déployant un petit cluster.

* **Action :** Téléchargement d'une image système légère (`alpine319`) et démarrage d'un cluster de 4 VM (Alpine Linux).
* **Vérification :** Validation du réseau interne via des requêtes ping vers les adresses IP allouées (192.168.56.10 à .40).
* **Nettoyage :** Destruction propre des VM pour libérer les ressources.

**Commandes :**
```bash
vagrant up
ping -c 1 -q 192.168.56.x
vagrant destroy -f
```

![Résultat du Test 01](Séance%201-Test01.png)

##  Test 02 : Déploiement d'un parc hétérogène

L'objectif était de simuler un environnement multi-systèmes représentatif de l'entreprise.

* **Action :** Téléchargement des box Vagrant de 4 distributions majeures :
  * **Rocky Linux 9** 
  * **Debian 12**
  * **OpenSUSE Leap 15**
  * **Ubuntu 22.04**
* **Exécution :** Lancement simultané de ces 4 systèmes via une seule commande.
* **Nettoyage :** Suppression de l'infrastructure de test après validation.

**Commandes :**
```bash
vagrant up
vagrant destroy -f
```

![Résultat du Test 01](Séance%201-Test02.png)

