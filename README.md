# Rapport-Test Technique pour le poste d’Administrateur Système et Sécurité Junior (Stage)



## Installation de ISPConfig

### Étape 2 : configurer le nom d'hôte et les hôtes

1. Vérification du nom d'hôte dans le /etc/hosts.
Il est important de configurer correctement le nom d'hôte et les hôtes pour éviter tout problème ultérieur lors de l'installation. Le nom d'hôte de nôtre serveur est un sous-domaine qui est:
```sh
nano /etc/host
```

2. Modification de /etc/hostname
Ajouter la partie sous-domais dans 
```sh
nano /etc/hostname
```

3. Rédemarrer les sytème avec 
```sh
sudo reboot
```

4. Après connection verifions si le nom d'hôte est correct.
```sh
hostname
hostname -f
```
![markdown](Images/hostname1)
### Étape 3 : Mise à jour système
Avant de procéder à l'installation, il est essentiel de mettre à jour les packages système avec la commande 
```sh
apt update && upgrade
```

### Étape 4 : Exécution du programme d'installation automatique

L'installateur automatique fournit un processus de configuration modulaire et facile à suivre. Il installe les progiciels nécessaires, notamment Apache2, PHP, MariaDB, Postfix, Dovecot, etc.

On peut choisir d'installer ISPConfig avec Apache ou Nginx comme serveur Web. Nous avons opté pour Nginx.

```sh
wget -O - https://get.ispconfig.org | sudo sh -s -- --use-nginx  --use-php=8.0 --use-ftp-ports=21-22 --lang=en --no-quota --unattended-upgrades
```
