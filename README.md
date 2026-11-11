# Infrastructure-PKI
Mise en place d'une infrastructure PKI avec OpenSSL, comprenant une CA racine, une CA intermédiaire, HTTPS, mTLS et la révocation des certificats.


 Présentation du projet

Ce projet consiste à concevoir et déployer une infrastructure PKI (Public Key Infrastructure) permettant de gérer la création, la distribution, la vérification et la révocation de certificats numériques.

L'objectif est de mettre en place une chaîne de confiance permettant de sécuriser les communications entre clients et serveurs grâce aux certificats numériques et au protocole TLS.

Objectifs:

Créer une autorité de certification racine (Root CA).
Créer une autorité de certification intermédiaire (Intermediate CA).
Générer et signer des certificats numériques avec OpenSSL.
Sécuriser un serveur web avec HTTPS et Nginx.
Mettre en place l'authentification mutuelle TLS (mTLS).
Gérer la révocation des certificats avec une CRL.
Vérifier le fonctionnement de la chaîne de confiance.

 Architecture de l'infrastructure:
 
Le laboratoire repose sur trois machines virtuelles
 Machine virtuelle:
 
VM "CAracine"  Création de l'autorité racine et signature de la CA intermédiaire 

VM "CAintermediate"  Délivrance et révocation des certificats 

VM "PKI"  Hébergement du serveur web HTTPS avec Nginx et mTLS 

 Technologies utilisées:

Debian 13: système d'exploitation des machines virtuelles.
OpenSSL: création, signature et gestion des certificats.
Nginx: serveur web et gestion des connexions HTTPS.
TLS 1.3: sécurisation des communications.
mTLS: authentification mutuelle entre client et serveur.
CRL: gestion des certificats révoqués.
RSA / SHA-256 / AES: algorithmes cryptographiques utilisés.

Fonctionnement de la chaîne de confiance
L'infrastructure repose sur deux autorités de certification :

1. La CA racine constitue l'autorité de confiance principale.
2. La CA intermédiaire est signée par la CA racine et délivre les certificats aux serveurs et aux clients.
La clé privée de la CA racine est protégée et conservée hors ligne après la signature de l'autorité intermédiaire.

Tests réalisés:
Trois scénarios ont été réalisés pour vérifier le fonctionnement de l'infrastructure :

 Connexion sans certificat client | HTTP 400 - Accès refusé 
 
 Connexion avec un certificat valide | HTTP 200 – Accès autorisé 
 
 Connexion avec un certificat révoqué | HTTP 400 – Accès refusé 

Les tests démontrent le bon fonctionnement de l'authentification mutuelle et de la révocation des certificats.
