# Harmonisation de l’antivirus des serveurs internationaux

## Contexte

À la suite du rachat de sites dans des pays européens, certains serveurs utilisaient encore les solutions antivirus historiques de ces entités.

Les abonnements correspondants avaient été conservés jusqu’à leur échéance. L’objectif était ensuite d’harmoniser ces serveurs avec le standard antivirus déjà utilisé par le reste du groupe, Windows Defender, avant une évolution ultérieure vers une solution EDR.

Le périmètre restant concernait un nombre limité de serveurs.

## Objectif

Migrer les derniers serveurs concernés vers le nouvel antivirus avant l’expiration de leurs anciens abonnements antivirus, tout en limitant les risques d’interruption de service.

## Mon rôle

J'étais chargée de coordonner le déploiement avec les équipes IT locales des deux sites européens.

Je n'étais pas responsable de la préparation technique de SCCM. Cette partie était réalisée par l'administrateur SCCM.

Mon rôle consistait principalement à :

* coordonner les différentes équipes impliquées ;
* communiquer les actions attendues aux équipes IT locales ;
* suivre l'avancement du déploiement ;
* organiser le passage des serveurs dans la collection SCCM prévue ;
* coordonner les redémarrages nécessaires ;
* vérifier la bonne installation du nouvel antivirus ;
* faire valider le bon fonctionnement des serveurs par les équipes locales.

## Parties prenantes

Les principaux interlocuteurs étaient :

* le responsable de l'équipe Infrastructure & Cybersecurity ;
* l'administrateur SCCM ;
* les équipes IT locales des deux sites européens.

Les équipes IT locales avaient une connaissance plus approfondie des serveurs concernés et intervenaient donc également dans la validation fonctionnelle après migration.

## Pilotage du projet

Le suivi du projet reposait principalement sur :

* des échanges par e-mail ;
* Microsoft Teams ;
* un tableau Excel de suivi.

Je transmettais aux équipes IT locales les consignes nécessaires pour chaque serveur et suivais avec elles les dates de migration.

Une fois les opérations réalisées, elles me confirmaient leur exécution et participaient à la validation du fonctionnement des serveurs.

Le projet devait être terminé avant l'expiration des abonnements aux anciennes solutions antivirus.

## Réalisation technique

Le déploiement de Windows Defender reposait sur SCCM.

Pour chaque serveur concerné :

1. l'ancien antivirus devait être désinstallé ;
2. le serveur était intégré à la collection SCCM préparée pour le déploiement ;
3. un redémarrage du serveur était réalisé ;
4. je vérifiais que Windows Defender était correctement installé et actif ;
5. je demandais à l'équipe IT locale de réaliser des tests afin de confirmer le bon fonctionnement du serveur.

Cette validation locale était importante car les équipes des sites connaissaient mieux les applications et usages associés à ces serveurs.

## Risques et contraintes

La principale contrainte identifiée concernait le redémarrage nécessaire des serveurs.

Il fallait donc coordonner les opérations avec les équipes locales afin que les redémarrages puissent être réalisés dans de bonnes conditions et que le fonctionnement du serveur puisse être vérifié immédiatement après.

Une autre contrainte était liée au calendrier : le basculement devait être réalisé avant l'expiration des abonnements aux solutions antivirus précédentes.

## Répartition des responsabilités

La préparation technique de SCCM était réalisée par l'administrateur en charge de cet outil.

De mon côté, j'assurais la coordination opérationnelle du déploiement entre l'équipe centrale et les équipes IT locales.

Cette organisation permettait de répartir les responsabilités en fonction des compétences de chacun :

* expertise SCCM pour la préparation du déploiement ;
* coordination et suivi pour l'organisation des migrations ;
* expertise locale pour la validation fonctionnelle des serveurs.

## Résultat

L'ensemble des serveurs concernés des sites européens a été migré vers Windows Defender avant la fin de mon alternance.

Le projet a ainsi permis d'harmoniser la protection antivirus de ces serveurs avec celle déjà utilisée par le reste du groupe.

## Retour d'expérience

Ce projet m'a permis de travailler sur un projet technique avec plusieurs équipes réparties dans différents pays.

J'ai notamment appris l'importance de répartir clairement les responsabilités entre les différents intervenants : l'équipe centrale apportait les outils et la coordination tandis que les équipes locales apportaient leur connaissance des serveurs et validaient leur fonctionnement après intervention.

Avec davantage d'expérience en gestion de projet, je formaliserais aujourd'hui davantage le suivi du déploiement, notamment avec :

* des critères de validation définis avant chaque migration ;
* un suivi formalisé des risques ;
* un statut clairement identifié pour chaque serveur ;
* une procédure de retour arrière définie avant intervention ;
* une synthèse de clôture du projet.

## Compétences mobilisées

### Gestion de projet

* Coordination d'équipes internationales
* Suivi d'avancement
* Gestion d'échéances
* Coordination d'interventions techniques
* Communication avec plusieurs parties prenantes
* Validation et clôture d'actions

### Techniques

* Windows Server
* Windows Defender
* SCCM
* Déploiement de logiciels
* Gestion d'antivirus

### Transverses

* Travail avec des équipes internationales
* Communication en anglais
* Coordination à distance
* Autonomie
* Collaboration avec des experts techniques
