# GamepadToPc
Host installer for the android app GamepadToPc

GamepadToPC

GamepadToPC est une application Python permettant de transformer un contrôleur de jeu Android en une manette de jeu virtuelle sur PC. Grâce à une communication UDP, l'application reçoit les entrées du contrôleur Android et les transmet à un serveur Python qui les interprète et les simule via vgamepad et ViGEmBus.


Connectez votre contrôleur de jeu (smartphone) Android au même réseau que votre PC.
Lancez l'application sur votre Android et configurez-la pour envoyer les données au serveur Python.
Serveur Python :

L'application Python écoute les paquets UDP entrants.
Les données reçues sont interprétées et traduites en actions de manette virtuelle.
Manette Virtuelle :

Les entrées sont transmises à vgamepad, qui simule une manette Xbox 360 via ViGEmBus.
Les jeux et applications sur PC reconnaissent la manette virtuelle comme une manette physique standard.


Installation
Prérequis
Système d'exploitation : Windows 10 ou supérieur.
Python : Version 3.10.6
ViGEmBus : Driver nécessaire pour la simulation de manettes virtuelles.

Installation via l'Installateur
L'installateur simplifie le processus d'installation en intégrant toutes les dépendances nécessaires.

Télécharger l'Installateur :

Accédez à la section Releases de ce dépôt.
Téléchargez le fichier GamepadToPC_Installer.exe.
Exécuter l'Installateur :

Double-cliquez sur GamepadToPC_Installer.exe.
Suivez les instructions à l'écran pour installer l'application.
Lancer l'Application :

Une fois l'installation terminée, lancez GamepadToPC Server depuis le menu Démarrer ou le raccourci sur le Bureau.
Installation Manuelle
Pour les utilisateurs avancés ou ceux souhaitant personnaliser l'installation.

Cloner le Dépôt :

bash
Copy code
git clone https://github.com/Snaaps/GamepadToPC.git
cd GamepadToPC
Installer les Dépendances Python : Assurez-vous d'avoir Python 3.10.6 installé. Ensuite, installez les packages requis :

bash
Copy code
pip install -r requirements.txt
Installer ViGEmBus :

Téléchargez le package ViGEmBus.
Exécutez l'installateur et suivez les instructions.
Configurer PyInstaller : Si vous souhaitez créer votre propre exécutable :

bash
Copy code
pyinstaller --onefile --windowed udp_server.py --add-binary "path\to\ViGEmClient.dll;vgamepad\win\vigem\client\x64\\" --name=GamepadToPC_Server
Utilisation
Lancer le Serveur :

Ouvrez GamepadToPC Server via le menu Démarrer ou le raccourci sur le Bureau.
Connecter le Contrôleur Android :

Assurez-vous que votre appareil Android est connecté au même réseau que votre PC.
Configurez l'application Android pour envoyer les données au serveur Python en utilisant l'adresse IP affichée dans l'interface.
Jouer :

Lancez votre jeu ou application sur PC.
Utilisez votre contrôleur Android comme une manette de jeu standard.
Dépannage
Problème : ViGEmClient.dll manquant
Solution :

Assurez-vous que ViGEmBus est correctement installé.
Vérifiez que ViGEmClient.dll est présent dans le répertoire :
vbnet
Copy code
C:\Users\haezs\AppData\Local\Programs\Python\Python310\lib\site-packages\vgamepad\win\vigem\client\x64\
Si la DLL est manquante, téléchargez-la depuis le dépôt officiel de ViGEmClient et placez-la dans le répertoire approprié.
Problème : Erreur de chargement des DLL Python
Solution :

Assurez-vous que python310.dll est inclus dans le build PyInstaller.
Recompilez l'application en utilisant le fichier .spec corrigé avec toutes les DLL nécessaires.
Utilisez Dependency Walker pour identifier toute DLL manquante.
Problème : L'application ne reconnaît pas la manette virtuelle
Solution :

Vérifiez que ViGEmBus est en cours d'exécution.
Redémarrez l'application GamepadToPC Server.
Assurez-vous que le contrôleur Android est correctement configuré pour envoyer les données.
Contribution
Les contributions sont les bienvenues ! Pour contribuer à ce projet, veuillez suivre les étapes suivantes :

Fork le Dépôt
Créer une Branche pour Votre Feature :
git checkout -b feature/nom-de-votre-feature

Committer Vos Changements :
git commit -m "Ajout de ma nouvelle feature"

Pousser vers la Branche :
git push origin feature/nom-de-votre-feature

Veuillez vous assurer que vos contributions respectent les standards de code du projet.

Licence
Ce projet est sous licence MIT. Voir le fichier LICENSE pour plus de détails.

Remerciements
PyInstaller pour l'empaquetage de l'application.
vgamepad pour la simulation de manettes de jeu virtuelles.
ViGEmBus pour le support des manettes virtuelles.
Toute la communauté Open Source pour les outils et les ressources utilisés dans ce projet.
Note : N'oubliez pas de remplacer les chemins et les liens par ceux correspondant à votre projet, comme le chemin vers le logo, les liens GitHub corrects, etc.
