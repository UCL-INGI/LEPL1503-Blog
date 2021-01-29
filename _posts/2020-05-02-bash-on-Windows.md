---
layout: post
title: Terminal Ubuntu sur Windows
author: Andru Onciul
---
Ce petit montre une manière d'éxecuter du code C depuis Windows sans passer par Virtualbox.

## Installer Ubuntu

1. Installer Ubuntu depuis le Windows Store

![Publish]({{ site.baseurl }}/images/UbuntuWindowsStore.png)

1.1. Si cette erreur apparait:

![Publish]({{ site.baseurl }}/images/ErreurSubSystemComponent.png)

taper cette ligne dans le powershell de windows (executer en tant que administrateur sinon cela ne marchera pas):
```Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux```

2. une fois ubuntu installé :

2.1 choisir un username (minuscule sans espaces)

2.2 un code (à ne pas perdre)

## Taper ces lignes de commandes dans Ubuntu

Pour la première fois sur le bash il va falloir installer le compilateur ainsi que
toutes les librairies qui seront utilisées dans les codes qui seront compilés.
Ces lignes de commandes ne devront être tapées que la première fois (tout reste installé même si le bash ubuntu est fermé)

```bash
sudo apt-get update                         		      #update toutes les libraires
# ubuntu demande le code du l’utilisateur du pc il suffit de le tapper et taper ENTER
sudo apt-get install build-essential		    #compilateur et debug (notamment commande gcc)
sudo apt-get install make			    #pouvoir utiliser des make
sudo apt-get install manpages-dev		    #documentation
```

Voici quelques librairies indispensables pour le projet à vous d'en mettre plus si besoin.
Il suffit de taper ubuntu install "nom de la librairie sur google" pour trouver la commande a taper

```bash
sudo apt-get install valgrind			    #valgrind
sudo apt-get install cppcheck 			    #cppcheck
sudo apt-get install libcunit1 libcunit1-doc libcunit1-dev 		#cunit
sudo apt-get install zlib1g-dev			    #librairies et headers
```

Maintenant pour accéder au dossier de votre projet

```cd /mnt/c                              #va sur le disque dur C: du pc```
![Publish]({{ site.baseurl }}/images/mountCs.png)

Vous êtes maintenant sur les fichiers du disque dur (C:) principal de votre PC.
Vous pouvez utiliser dans ce bash comme le bash d'un système UNIX puisque c'en est un.

## Exécuter la commande du makefile comme dans un terminal Linux

Maintenant il vous suffit d’ouvrir Ubuntu et de taper ceci à chaque fois que vous voulez lancer votre code :

```bash
cd /mnt/c                               #va sur le disque dur C: du pc
cd “fichier ou ya le projet”    		      #rentre dans le bon fichier
make fact
./fact -N 4 input.txt output.txt
```
