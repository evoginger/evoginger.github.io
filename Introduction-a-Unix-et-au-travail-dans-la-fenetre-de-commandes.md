---
title: Introduction à Unix et au travail dans la fenêtre de commandes
date: 2017-11-01 21:42:02
tags:
---
# <p align="center"> Récapitulatif de la séance 2 (27/09/2017) </p>

<div align="center">

![linux_icone](https://user-images.githubusercontent.com/33186097/32147702-b11163a2-bceb-11e7-86ac-f2961069d61d.png)

</div>

## PLAN DU COURS
### I COMPARAISON
- Arborescence de stockage (Unix, Windows et Mac OS)
- Chemin
### II COMMANDES A RETENIR
- Caractères spéciaux :  1) /;  2) .;  3) ..;  4)~
- Commandes :  1) pwd;  2) cd;  3) ls;  4) mkdir;  5) man;  6) touch;  7) echo;  8) date;  9) wc;  10) cat
### III REDIRECTION

##  I COMPARAISON
### 1.1 Arborescence de stockage
#### 1.1.1 Windows
Chaque partition a une racine, désignée par “\”
  **EX :** C:\
#### 1.1.2 Unix (distribution Linux Ubuntu)
Un répertoire peut contenir des fichiers et d’autres répertoires (cf. dossiers de MS-DOS).
Les répertoires sont organisés en arbre. Ils sont organisés dans un répertoire appelé la racine, qui a une référence unique : “/”.
  **EX1 :** dans /
`$ tree -L 1 -d`

````
.
├── bin
├── boot
├── cdrom
├── dev
├── etc
├── home
├── lib
├── lib64
├── lost+found
├── media
├── mnt
├── opt
├── proc
├── root
├── run
├── sbin
├── snap
├── srv
├── sys
├── tmp
├── usr
└── var

22 directories
````
**EX2 :** dans /usr
````
.
├── bin
├── games
├── include
├── lib
├── local
├── locale
├── sbin
├── share
└── src

9 directories
````

 Chaque répertoire contient deux répertoires spéciaux :
- le répertoire courant “.”
- le parent du répertoire “..”

### 1.2 Chemin
#### 1.2.1 Chemin absolu
Une référence commençant par “/” : le moyen pour désigner une ressource de manière non ambïgue  
  **EX :** 
  1)/usr/bin/   2)/usr/bin   3)/usr/bin/.  désignent la même référence
/usr/bin/.. désigne son parent, i.e.  /usr
        
#### 1.2.2 Chemin relatif
Une référence ne commençant pas par “/” : le système nous permet d'utiliser une référence par rapport au répertoire courant.

## II COMMANDES A RETENIR
### 2.1 caractères spéciaux
#### 2.1.1  /
Dans  /usr/bin/
Le premier “/” : la racine.
Le deuxième “/” : séparateur entre des répertoires.  

#### 2.1.2  .  et  ..
cf 1.1.2

#### 2.1.3 ~
Le répertoire principal.

### 2.2 commandes
Syntax générale d'une commande unix :    
`$ nom_commande   [- OPTION]   [ARGUMENTS]`

#### 2.2.1 $pwd
**P**rint **W**orking **D**irectory
Le répertoire où je me trouve
**EX :**
````
yizhou@yizhou-ThinkPad-T440p:~/Documents$ pwd
/home/yizhou/Documents
````
#### 2.2.2 $cd
**C**hange **D**irectory
Positionner / changer le repertoire de travail
**EX :**
````
chunyang@chunyang-ThinkPad:~$ cd Documents/ProjetEncadre20172018/
chunyang@chunyang-ThinkPad:~/Documents/ProjetEncadre20172018$ cd
````
*Avant d'aller dans un répertoire, il faut s'assurer que cet endroit existe.*

#### 2.2.3 $ls [OPTION]... [FILE]...
**LI**st
Afficher le contenu d'un répertoire
`$ ls -l`  
Afficher le type du fichier, les permissions d'accès, le nombre de liens physiques, le nom du propriétaire et du groupe, la taille en octets et l'horodatage de la dernière modification.
**EX :**
````
$ ls -l

total 128
drwxr-xr-x   2 root root  4096 sept. 26 20:15 bin
drwxr-xr-x   3 root root  4096 sept. 27 08:24 boot
drwxrwxr-x   2 root root  4096 sept. 16 13:30 cdrom
drwxr-xr-x  21 root root  4260 oct.   1 19:29 dev
drwxr-xr-x 137 root root 12288 sept. 27 08:31 etc
drwxr-xr-x   3 root root  4096 sept. 16 13:31 home
lrwxrwxrwx   1 root root    33 sept. 27 08:23 initrd.img -> boot/initrd.img-4.10.0-35-generic
lrwxrwxrwx   1 root root    33 sept. 16 13:32 initrd.img.old -> boot/initrd.img-4.10.0-28-generic
drwxr-xr-x  24 root root  4096 sept. 16 14:37 lib
drwxr-xr-x   2 root root  4096 août   1 13:19 lib64
drwx------   2 root root 16384 sept. 16 13:22 lost+found
drwxr-xr-x   3 root root  4096 sept. 19 22:35 media
drwxr-xr-x   2 root root  4096 août   1 13:17 mnt
drwxr-xr-x   4 root root  4096 sept. 16 13:37 opt
dr-xr-xr-x 248 root root     0 oct.   1 19:29 proc
drwx------   4 root root  4096 sept. 16 15:55 root
drwxr-xr-x  26 root root   840 oct.   1 19:30 run
drwxr-xr-x   2 root root 12288 sept. 26 20:15 sbin
drwxr-xr-x   2 root root  4096 avril 29 10:38 snap
drwxr-xr-x   2 root root  4096 août   1 13:17 srv
dr-xr-xr-x  13 root root     0 oct.   1 19:29 sys
drwxrwxrwt  12 root root 32768 oct.   1 20:06 tmp
drwxr-xr-x  11 root root  4096 août   1 13:24 usr
drwxr-xr-x  14 root root  4096 août   1 13:34 var
lrwxrwxrwx   1 root root    30 sept. 27 08:23 vmlinuz -> boot/vmlinuz-4.10.0-35-generic
lrwxrwxrwx   1 root root    30 sept. 16 13:32 vmlinuz.old -> boot/vmlinuz-4.10.0-28-generic
````
#### Spécification :
`1drwxr-xr-x   2 root root  4096 sept. 26 20:15 bin`
- **d :** dossier 
- **droit groupe :**
                     utilisateur ;
                     groupe ;
                     autre utilisateurs
- **permissions :**
                     [r] : read;
                     [w] : write;
                     [x] : execute, access to the directory
- utilisateur hérite le droit du goupe où il appartient
- [-] absence de droit  

#### 2.2.4 $mkdir [OPTION]... DIRECTORY...
**M**a**K**e **DIR**ectory
Créer un répertoire
**EX :**
````
$ mkdir TOTO
$ mkdir toto
$ mkdir tOtO

3 répertoires différents sont créés
````

#### 2.2.5 $man
**MAN**ual
Afficher le manuel d'une commande

#### 2.2.6 $touch [OPTION]... FILE…
Creer un fichier s'il n'existe pas

#### 2.2.7 $date
Afficher la date
**EX :**
````
$date
dimanche 1 octobre 2017, 21:11:13 (UTC+0200)
````


#### 2.2.8 $echo [SHORT-OPTION]... [STRING]...
Afficher sur le console ce que l'on a écrit en ajoutant un retour à la ligne

#### 2.2.9 $wc
**W**ord **C**ount
Afficher le nombre de lignes, de mots, de caractères et d'octets
OPTION :
       [-l]nb de lignes; 
       [-w]nb de mots;
       [-m]nb de caractères;
       [-c] nb d'octets

#### 2.2.10 $cat [OPTION]... [FILE]...
Concatenate files and print on the standard output

## III REDIRECTION (à compléter pour la séance [3](https://github.com/win-gin/PROJET_MOT_SUR_LE_WEB/issues/3) )

## REFERENCES :
- [http://www.tal.univ-paris3.fr/cours/Plurital_Formation_Unix.pdf](http://www.tal.univ-paris3.fr/cours/Plurital_Formation_Unix.pdf)
- [http://www.linux-france.org/article/man-fr/man1/Index-1.html](http://www.linux-france.org/article/man-fr/man1/Index-1.html)