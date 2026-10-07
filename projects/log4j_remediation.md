# Gestion de la vulnérabilité Log4j

## Contexte

Lors de la divulgation de la vulnérabilité Log4j, le sujet a rapidement pris une importance majeure dans l'actualité cybersécurité.

Après avoir constaté les nombreuses alertes autour de cette vulnérabilité, j'ai interrogé mon responsable sur une éventuelle exposition de notre environnement.

Après des recherches complémentaires, nous avons identifié que certaines applications ou certains serveurs pouvaient effectivement être concernés.

Le sujet a alors été traité comme une urgence par l'équipe Infrastructure & Cybersecurity.

## Objectif

Identifier rapidement les applications et serveurs potentiellement concernés par la vulnérabilité Log4j, mettre en place les mesures de protection disponibles et suivre les corrections jusqu'à clôture du sujet.

## Mon rôle

Le traitement de la vulnérabilité a été réalisé principalement avec :

* le responsable de l'équipe Infrastructure & Cybersecurity ;
* l'administrateur systèmes ;
* moi-même.

Nos activités habituelles ont été temporairement interrompues afin de prioriser cette remédiation.

Mon rôle comprenait notamment :

* la participation au recensement des applications et serveurs potentiellement concernés ;
* le suivi des versions applicatives ;
* la tenue du tableau de suivi ;
* la mise en œuvre de certaines mesures de contournement ;
* la réalisation de certaines mises à jour ;
* le suivi des actions réalisées par l'administrateur systèmes ;
* le reporting auprès de mon responsable.

## Identification des systèmes concernés

Avec mon responsable et l'administrateur systèmes, nous avons recensé les logiciels présents dans l'environnement et cherché à déterminer, en fonction des produits et de leurs versions, lesquels pouvaient être concernés par Log4j.

Le périmètre comprenait des environnements Windows et Linux.

L'une des principales difficultés était l'identification précise des versions utilisées.

Dans certains cas, il était difficile de déterminer nous-mêmes si une application embarquait une version vulnérable de Log4j.

Nous nous appuyions alors sur les informations fournies par les éditeurs.

Il est notamment arrivé que nous pensions initialement qu'un serveur pouvait être vulnérable avant que l'éditeur confirme finalement que le produit concerné ne l'était pas.

## Suivi de la remédiation

Un tableau Excel a été utilisé pour centraliser le suivi des systèmes concernés.

Il permettait notamment de suivre :

* les serveurs ou applications identifiés ;
* la mise en place éventuelle d'une mesure de contournement ;
* la disponibilité d'une mise à jour ;
* l'état d'application du correctif.

L'administrateur systèmes réalisait également des recherches auprès des éditeurs et me transmettait les informations obtenues afin que le suivi puisse être mis à jour.

Un reporting régulier était réalisé auprès de mon responsable.

## Remédiation

Lorsque des correctifs étaient disponibles, les serveurs ou applications concernés étaient mis à jour.

Les actions étaient réparties entre l'administrateur systèmes et moi-même.

Pour au moins l'un des systèmes concernés, aucune mise à jour n'était encore disponible.

J'ai alors appliqué une mesure de contournement temporaire permettant de réduire l'exposition en attendant la publication d'un correctif par l'éditeur.

Une fois les correctifs publiés, les mises à jour correspondantes ont pu être appliquées.

## Gestion de l'urgence

La vulnérabilité Log4j a nécessité de modifier immédiatement les priorités de l'équipe.

Les activités prévues ont été interrompues afin de concentrer les efforts sur :

* l'identification des systèmes potentiellement vulnérables ;
* la recherche d'informations auprès des éditeurs ;
* la mise en place de mesures temporaires ;
* l'application des correctifs ;
* le suivi de la remédiation.

Le manque initial de visibilité sur les applications réellement concernées constituait l'une des principales difficultés du sujet.

## Difficultés rencontrées

### Manque de visibilité

L'une des difficultés principales était de déterminer rapidement quelles applications utilisaient réellement une version vulnérable de Log4j.

La présence de logiciels tiers et la difficulté à identifier certaines versions rendaient cette analyse complexe.

### Dépendance aux éditeurs

Dans certains cas, il était nécessaire d'attendre la confirmation d'un éditeur pour déterminer si un produit était vulnérable ou non.

Il fallait également attendre la disponibilité de certains correctifs.

### Absence immédiate de correctifs

Lorsqu'un patch n'était pas encore disponible, des mesures de contournement temporaires devaient être appliquées afin de réduire le risque jusqu'à la publication d'une mise à jour.

## Résultat

Le recensement des applications et serveurs potentiellement concernés a été réalisé et les différentes actions de remédiation ont été suivies jusqu'à leur clôture.

Les systèmes nécessitant une correction ont été mis à jour lorsque les correctifs sont devenus disponibles.

Des mesures temporaires ont été utilisées lorsque cela était nécessaire.

Le traitement de la vulnérabilité était terminé avant la fin de mon alternance.

## Retour d'expérience

Cet épisode m'a particulièrement sensibilisée à la difficulté de gérer une vulnérabilité critique lorsqu'on ne dispose pas immédiatement d'une vision complète des composants utilisés dans le système d'information.

Avec davantage d'expérience, je chercherais aujourd'hui à disposer en amont :

* d'un inventaire applicatif plus précis ;
* d'une meilleure visibilité sur les versions déployées ;
* d'un référentiel des propriétaires des différentes applications ;
* d'une procédure formalisée de traitement des vulnérabilités critiques ;
* de critères permettant de prioriser les systèmes selon leur exposition et leur criticité ;
* d'un tableau de suivi standardisé pour la remédiation ;
* d'une procédure de validation après correction.

Ce projet m'a également montré l'importance de pouvoir réorganiser rapidement les priorités d'une équipe lorsqu'une vulnérabilité critique apparaît.

## Compétences mobilisées

### Gestion de crise / projet

* Priorisation en situation d'urgence
* Suivi d'actions de remédiation
* Coordination avec une équipe technique
* Reporting
* Gestion de dépendances externes
* Suivi jusqu'à clôture

### Cybersécurité

* Gestion de vulnérabilités
* Analyse d'exposition
* Mesures de contournement
* Suivi de correctifs
* Veille cybersécurité
* Remédiation

### Techniques

* Windows Server
* Linux
* Gestion des mises à jour
* Analyse de versions applicatives

### Transverses

* Réactivité
* Autonomie
* Travail en équipe
* Recherche d'information
* Adaptation des priorités
* Gestion de l'incertitude
