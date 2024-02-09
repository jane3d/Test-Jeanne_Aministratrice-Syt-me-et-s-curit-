# Rapport-Test Technique pour le poste d’Administrateur Système et Sécurité Junior (Stage)



## ISPConfig

### Étape 1 : Connexion au serveur
```ssh -i JeanneTestHR.pem ubuntu@jeanne-test-srv-01.cyberspector.xyz
```

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
![markdown](https://github.com/jane3d/Test_Jeanne_Aministratrice-Syteme-et-securite/assets/93372228/b7aebc5f-1d8c-4a75-8f14-2d1d9800c458)

Après installation nous avons avons le mot de passe pour ce connecter à notre serveur isp à l'adresse https://jeanne-test-srv-01.cyberspector.xyz:8080/index.php
```sh
[INFO] Installation ready.
[INFO] Your ISPConfig admin password is: QTjb1aUtGqjWjs2
[INFO] Your MySQL root password is: wKHxGADfrNGA2xJ6RRMT
[INFO] Warning: Please delete the log files in /tmp/ispconfig-ai/var/log/setup-* once you don't need them anymore because they contain your passwords!
```
![markdown](https://github.com/jane3d/Test_Jeanne_Aministratrice-Syteme-et-securite/assets/93372228/eac5b661-16c7-45a6-8d05-19bfe29d42db)

## Configurer un nom de domaine et un mail sur ISPConfig
1. Création du client

Client->Add new client 
![markdown](https://github.com/jane3d/Test_Jeanne_Aministratrice-Syteme-et-securite/assets/93372228/9d4594cb-3dbe-40ab-ae78-4309c1486c0f)

2. Création du site
Sites->Add new site
![markdown](https://github.com/jane3d/Test_Jeanne_Aministratrice-Syteme-et-securite/assets/93372228/73b5a085-92f7-4e1d-af0c-222a7d221d6c)

3. Création de la base de donné
Sites->Databases-> Add new Database
![markdown](https://github.com/jane3d/Test_Jeanne_Aministratrice-Syteme-et-securite/assets/93372228/be280269-f273-4647-b20e-a2410d66a391)

3. Création de l'utilisateur de la base de donnée

Sites->Databases Users -> Add new User

![markdown](https://github.com/jane3d/Test_Jeanne_Aministratrice-Syteme-et-securite/assets/93372228/e0ce7730-19ff-47a3-8a15-65500b84d74d)

5. Création d'un utilisation FTP
   
Sites->FTP Account -> Add new FTP-User
![markdown](https://github.com/jane3d/Test_Jeanne_Aministratrice-Syteme-et-securite/assets/93372228/a64c79da-0bae-4c66-a307-1e53cd664cc5)

  
3. Configuration du DNS Zones

DNS->Add new DNNS zone with wizard

![markdown](https://github.com/jane3d/Test_Jeanne_Aministratrice-Syteme-et-securite/assets/93372228/8acd65bf-1577-4c06-b715-d9e8eabb4f65)

On peut desormais acceder à domaine via http

![markdown](https://github.com/jane3d/Test_Jeanne_Aministratrice-Syteme-et-securite/assets/93372228/56da48d8-06df-4076-8531-2ff8941e8719)

6. Création de l'adress email

-Ajout du domain Email-> Add new domain

![markdown](https://github.com/jane3d/Test_Jeanne_Aministratrice-Syteme-et-securite/assets/93372228/fd57aeb5-1b41-496e-8bf2-2843fbf9ab8d)

-Email-> Emailbox-> add new mail box
![markdow](https://github.com/jane3d/Test_Jeanne_Aministratrice-Syteme-et-securite/assets/93372228/43c1d1cc-c65b-4aa6-9193-74c2ad948cde)

-Verification du mail.
Nous pouvons envoyer et recevoir de message avec nôtre adresse mail
![markdown](https://github.com/jane3d/Test_Jeanne_Aministratrice-Syteme-et-securite/assets/93372228/a7b334ee-b0f4-411a-8548-707e2861399b)

## Configuration d'un site wordpress sur le nom de domaine
### Étape 1: Configurer NGINX pour WordPress
Pour commencer, créeons le dossier racine de notre installation WordPress.
```sh
mkdir -p /var/www/html/wordpress/public_html
```
Pour créer un bloc de serveur NGINX pour notre domaine WordPress, accédons au /etc/nginx/sites-availabledossier. Il s'agit de l'emplacement par défaut des blocs du serveur NGINX. 
```sh
cd /etc/nginx/sites-available
nano  wordpress.conf
```
![markdown](https://github.com/jane3d/Test_Jeanne_Aministratrice-Syteme-et-securite/assets/93372228/a54c4e33-9073-4196-9042-335dbb0e6529)

### Étape 2 : Téléchargez et configurez WordPress
Dans cette étape, téléchargeons le fichier WordPress archivé à l'aide wget et décompressez-le à la racine de l'installation WordPress que nous avons créée à l'étape précédente. Pour ce faire, exécutez les commandes suivantes depuis le terminal. Ainsi que les propriété nécessaire aux fichiers
```sh
cd /var/www/html/wordpress/public_html
wget https://wordpress.org/latest.tar.gz
tar -zxvf latest.tar.gz
mv wordpress/* .
rm -rf wordpress
cd /var/www/html/wordpress/public_html
chown -R www-data:www-data *
chmod -R 755 *
```

Nous avons founit  le nom de la base de données, l'utilisateur de la base de données et le mot de passe dans le fichier de configuration WordPress afin qu'il puisse se connecter à la base de données Mysql que nous avions créée précédemment. Par défaut, WordPress fournit un exemple de fichier de configuration et nous l'utiliserons pour créer notre propre fichier de configuration.

### Étape 3 : Installez WordPress

Pour terminer l'installation de WordPress, nous avons accedé à notre navigateur sur cyber-spector.iuc et suivi les étapes décrites ci-dessous.

![markdown](https://github.com/jane3d/Test_Jeanne_Aministratrice-Syteme-et-securite/assets/93372228/50bf128f-4b92-4d4e-81ca-43aeb09af373)

![markdown](https://github.com/jane3d/Test_Jeanne_Aministratrice-Syteme-et-securite/assets/93372228/f31b70a4-2cad-46a5-a7de-00cbbafe74ed)

Après cela nous pouvons accéder à notre site web.

![markdown](https://github.com/jane3d/Test_Jeanne_Aministratrice-Syteme-et-securite/assets/93372228/55ed9dff-6908-4587-ae42-6ce853087f3a)
![markdown](https://github.com/jane3d/Test_Jeanne_Aministratrice-Syteme-et-securite/assets/93372228/075e85f5-6c44-4eff-8aa7-b85bcedb1156)

## Installation de wazuh
Pour installer wazuh nous avons suivicla documentation officiel: https://documentation.wazuh.com/current/installation-guide/wazuh-server/step-by-step.html

L'installation de l'agent c'est fait sur le serveur dans Agent add new Agent

Quelques images 

![markdown](https://github.com/jane3d/Test_Jeanne_Aministratrice-Syteme-et-securite/assets/93372228/ea0d24bc-d197-4b00-8fbd-34aeafcf48cd)
![markdwon](https://github.com/jane3d/Test_Jeanne_Aministratrice-Syteme-et-securite/assets/93372228/eb814971-9f5e-4ac7-9a52-d707a7816141)
![markdown](https://github.com/jane3d/Test_Jeanne_Aministratrice-Syteme-et-securite/assets/93372228/8291e570-f781-4c10-8029-0114d19ec20f)

![markdown](https://github.com/jane3d/Test_Jeanne_Aministratrice-Syteme-et-securite/assets/93372228/12dfdf51-5d60-466b-812e-8f6de9bc5676)
![markdown](https://github.com/jane3d/Test_Jeanne_Aministratrice-Syteme-et-securite/assets/93372228/eaa16bdb-4388-429d-966d-455b0c411a8e)



