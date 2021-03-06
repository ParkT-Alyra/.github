# ParkT
***Un système de reservation de parking intelligent décentralisé réalisé avec Truffle et Solidity***

## Introduction

Le projet ParkT consiste à mettre à disposition de conducteurs recherchant une place, des parkings privés.
Pour ce faire, un propriétaire de parking renseigne les informations de son parking :

    * L'addresse du wallet du propriétaire
    * Un prix à la seconde
    * Un prix correspondant au dépot de garantie (en cours)
    * Des coordonnées précises de la localisation du parking (coordonnées GPS)
    * Un code postal permettant de faire la recherche des parkings à proximité via le front
    * Configuration de l'IOT (en cours)
    * Configuration de la barrière (encours)

## Fonctionnalités

### Enregistrement d'un parking par un propriétaire

    On utilisera les données précitées pour enregistrer le parking

### Reservation d'un parking par un conducteur

Pré-requis: un wallet (il n'est pas nécessaire d'être enregistré sur l'application)

	Le conducteur, au travers d'une interface peut rechercher les parkings à proximité par code postal (en cours)
	L'existence du parking est vérifié
	La disponibilité du parking est vérifié
	Le montant de la reservation pour la journée doit être envoyé lors de la réservation

    Une fois les conditions remplies, le parking est réservé et les informations d'accès au parking
    sont transmis au conducteur.

    La blockchain est mise à jour avec l'heure du début de réservation

### Fin de la réservation

    On vérifie que l'utilisateur qui appelle la fonction releaseParking est bien celui qui a réservé (couplé à l'IOT)
    On arrête le compteur pour le paiement de la réservation
    On séquestre le montant qui doit être payé au propriétaire
    On rend les fonds non utilisés au conducteur

### Mise à disposition des fonds pour le propriétaire

    Afin de répondre aux exigences de sécurité, une fonction withdraw permet au propriétaire de récupérer
    ses recettes.
    On s'assure que c'est bien le propriétaire qui accède à cette fonction
    On met à jour la balance avant de transférer les fonds


## README du contrat parkT

   [NatSpec ParkT.sol](https://htmlpreview.github.io/?https://github.com/ParkT-Alyra/parkT/blob/main/ParkT.html)
   
## Tools Required:

Avant de cloner le repository, assurez-vous d'avoir installé :

* Solidity
* Ganache
* Truffle
* Box react de truffle
* Node Package Manager
* Node.js
* MetaMask

## Pour démarrer <a name="getting-started"></a>

Cloner le repo : 

`git clone https://github.com/ParkT-Alyra/parkT`

Une fois le repo cloné :
	
	npm install

Pour installer les dépendances permettant le lancement de truffle ainsi que les tests (hdwallet, openzeppelin, dotenv).

Ensuite, déplacez-vous dans le répertoire client. Dans votre terminal/ligne de commande, exécutez :

	npm install (dépendance front)

	truffle test
	
## Démarrer l'application en local:

	npm start
	
## Déployer le SC sur Ropsten

	truffle migrate --network ropsten
	
## Déployer le front sur gitHub Pages
	
	npm deploy

