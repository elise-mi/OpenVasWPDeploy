# OpenVasWPDeploy
**Ce dépôt contient des instructions pour déployer OpenVAS sur Windows et Linux à l'aide de Vagrant et VirtualBox.**

## 🛠️Windows : 


1.  **Installer Vagrant** en téléchargeant l'installeur depuis le site officiel [ICI](https://releases.hashicorp.com/vagrant/2.3.7/vagrant_2.3.7_windows_amd64.msi)

2. **Installer virtualbox 6.1.44** [ICI](https://download.virtualbox.org/virtualbox/6.1.44/VirtualBox-6.1.44-156814-Win.exe)

3. **Installer la dépendance VirtualBox CA Certificate** en suivant les instructions disponibles [ICI](https://download.virtualbox.org/virtualbox/6.1.44/Oracle_VM_VirtualBox_Extension_Pack-6.1.44.vbox-extpack)

4. **Télécharger un certificat**[ICI](https://curl.se/ca/cacert-2023-05-30.pem)

5.  **Copier**  le dans votre dossier puis faites en un raccourci 
6. **Copier le chemin** entier de votre raccourci *(clique droit -> proprieté -> Emplacement :* )

7. Rechercher `Variables` dans la barre de recherche Windows puis cliquer sur `Modifier les variables d'environements`
8. Cliquer sur `Variable d'environement`
9. Faites en une nouvelle dans la partie `Variables Utilisateur`

10. Donner comme nom : `SSL_CERT_FILE `
11. Mettre le chemin du raccourci que vous avez auparavant copié dans `Valeur de la Variable`
12. **Télécharger ce dépôt** en allant sur le site suivant le télécharger : https://github.com/Benji63/OpenVasWPDeploy
13. **Puis le dézipper** dans le dossier de votre choix !
14. **Générer une paire de clées SSH** en exécutant la commande suivante dans un **Powershell** en administrateur :
ssh-keygen -t rsa -b 4096 -f $HOME\.ssh\id_rsa

15. Si code d'erreur il faudra créer un dossier dans votre répertoire utilisateur avec comme nom : `.ssh`

16. **Aller dans le dossier du projet**

17. Lancer en administrateur : `LaunchVagrant.bat`

18. Vous n'avez plus qu'à attendre la fin de la création des machines et de l'éxécution des scripts puis regardez dans la boîte mail paramétrée que vous avez bien reçu le rapport par mail ! 

## 🛠️Linux

#### Ce tuto se realisera sous une distrubution UbuntuDesktop

1. Recuperer les paquets VirtualBox :


```
 wget -O-https://www.virtualbox.org/download/oracle_vbox_2016.asc | sudo gpg --dearmor --yes --output /usr/share/keyrings/oracle-virtualbox-2016.gpg
```


2. Specifier des chemins d'acces au paquet pour les commande `apt` :

```
echo "deb [signed-by=/usr/share/keyrings/oracle-virtualbox-2016.gpg] http://download.virtualbox.org/virtualbox/debian $(lsb_release -sc) contrib" | sudo tee /etc/apt/sources.list.d/virtualbox.list
```
3. Installer le logiciel VirtualBox

```
sudo apt install virtualbox-6.1

sudo apt --fix-broken install

sudo apt install virtualbox-6.1
```

4. Installer les extensions de VirtualBox 

```
https://download.virtualbox.org/virtualbox/6.1.44/Oracle_VM_VirtualBox_Extension_Pack-6.1.44.vbox-extpack
```
5. Installer Vagrant :

```
curl -O https://releases.hashicorp.com/vagrant/2.2.9/vagrant_2.2.9_x86_64.deb
```

```
sudo apt install ./vagrant_2.2.9_x86_64.deb
```
```
vagrant --version
```

6. Lancer virtual box, cliquer sur préférences 

    - Aller dans extensions

    - Cliquer sur plus, puis ajouter l'extension pack telechargée auparavant
    - Fermer virtual box

7. Faire la mise à jour des paquets

```
sudo apt update | apt upgrade
```
8. Installer enfin le pack d'extension de VirtualBox : 
 
```
sudo apt install virtualbox-ext-pack Relancer virtual box elles est installée
```

9. Télécharger le certificat depuis le naviguateur :  (https://curl.se/ca/cacert-2023-05-30.pem)

10. **Depuis un CMD** mettre le path jusqu au certificat en tant que variable d'environnement
```
SSL_CERT_FILE=PATHTOCERT
```
    
11. **Générer la paire de clée SSH depuis un cmd**

```
ssh-keygen -t rsa -b 4096 -f $HOME\.ssh\id_rsa
```
12. Intaller Git

```
sudo apt install git
```
13. Enfin cloner le projet dans le dossier de votre choix (via la commande `cd`): 

```
git clone https://github.com/Benji63/OpenVasWPDeploy
```
14. Aller dans le dossier 

```
cd OpenVasWPDeploy
```
15. Lancer la commande : 

```
LaunchVagrantLinux.sh
```

16. Vous n'avez plus qu'à attendre la fin de la création des machines et de l'éxécution des scripts puis regardez dans la boîte mail paramétrée que vous avez bien reçu le rapport par mail ! 



        
