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
![markdown](https://github.com/jane3d/Test_Jeanne_Aministratrice-Syteme-et-securite/assets/93372228/5e3216b1-a9c5-4db2-a3c4-fb91802797f3)
)
![markdown](https://github.com/jane3d/Test_Jeanne_Aministratrice-Syteme-et-securite/assets/93372228/abbad846-413e-4716-a769-8954ce4010e0)

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
![markdown](github.com/jane3d/Test_Jeanne_Aministratrice-Syteme-et-securite/assets/93372228/b7aebc5f-1d8c-4a75-8f14-2d1d9800c458)

Après installation nous avons avons le mot de passe pour ce connecter à notre serveur isp à l'adresse https://jeanne-test-srv-01.cyberspector.xyz:8080/index.php
```sh
[INFO] Installation ready.
[INFO] Your ISPConfig admin password is: QTjb1aUtGqjWjs2
[INFO] Your MySQL root password is: wKHxGADfrNGA2xJ6RRMT
[INFO] Warning: Please delete the log files in /tmp/ispconfig-ai/var/log/setup-* once you don't need them anymore because they contain your passwords!
```
![markdown](https://github.com/jane3d/Test_Jeanne_Aministratrice-Syteme-et-securite/assets/93372228/eac5b661-16c7-45a6-8d05-19bfe29d42db)

## Configurer un nom de domaine et un mail sur ISPConfig
