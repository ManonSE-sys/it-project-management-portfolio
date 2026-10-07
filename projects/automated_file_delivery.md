# Automatisation de la collecte et de la mise à disposition de fichiers

## Contexte

Un utilisateur interne réalisait quotidiennement plusieurs opérations manuelles afin de récupérer des fichiers depuis différentes sources accessibles par URL.

Les fichiers étaient téléchargés régulièrement, puis regroupés et compressés avant d'être transmis à un autre service.

Ce processus nécessitait plusieurs manipulations répétitives et mobilisait inutilement du temps.

Avec un collègue, nous avons proposé d'automatiser la majeure partie de cette chaîne afin de limiter les interventions manuelles.

## Objectif

Automatiser la récupération, le traitement et la mise à disposition des fichiers afin que l'utilisateur n'ait plus qu'à récupérer l'archive finale et la transmettre au service concerné.

L'automatisation devait permettre de :

- récupérer quotidiennement les fichiers depuis plusieurs URL ;
- préparer automatiquement les données collectées ;
- générer une archive hebdomadaire ;
- renommer les fichiers selon le format attendu ;
- mettre l'archive à disposition sur un espace de stockage NFS ;
- nettoyer les fichiers devenus inutiles ;
- superviser le bon déroulement du traitement.

## Mon rôle

J'ai pris en charge la conception et la mise en œuvre de l'automatisation.

Mes activités comprenaient notamment :

- l'analyse du processus manuel existant ;
- la définition des différentes étapes à automatiser ;
- le développement du script Bash ;
- la planification de son exécution ;
- les tests du traitement ;
- la mise en production ;
- la mise en place de la supervision ;
- la documentation de la solution ;
- la validation du résultat avec l'utilisateur.

## Fonctionnement de l'automatisation

L'automatisation reposait sur un script Bash exécuté automatiquement via `cron`.

Le traitement réalisait notamment :

1. la récupération des fichiers depuis plusieurs URL ;
2. leur stockage local ;
3. leur regroupement et leur compression ;
4. le renommage de l'archive ;
5. sa copie vers un espace de stockage NFS ;
6. le nettoyage des fichiers devenus inutiles.

La récupération était réalisée quotidiennement.

Une archive regroupant les données collectées était ensuite générée de manière hebdomadaire et mise à disposition de l'utilisateur sur le stockage partagé.

## Supervision

Afin de ne pas laisser fonctionner l'automatisation sans contrôle, j'ai également intégré son suivi dans Nagios.

Le traitement générait des informations permettant de connaître son état.

Un contrôle dédié analysait les informations produites par le script afin de déterminer si l'exécution s'était correctement terminée.

Selon le contenu détecté, la supervision retournait notamment :

- un état `OK` lorsque le traitement s'était correctement déroulé ;
- un état `CRITICAL` lorsqu'un problème était détecté.

La mise en place de cette supervision a constitué l'une des parties les plus intéressantes du projet, car je n'avais encore jamais développé de contrôle reposant sur l'analyse du contenu généré par un traitement automatisé.

## Tests et validation

Avant la mise en production, le script a été exécuté manuellement afin de vérifier chaque étape du processus.

Le résultat obtenu a ensuite été comparé au processus manuel précédent.

L'utilisateur concerné a également participé à la validation afin de confirmer que :

- les fichiers attendus étaient bien récupérés ;
- l'archive produite était exploitable ;
- sa mise à disposition correspondait à son besoin.

Une fois ces validations réalisées, l'exécution automatique a été activée.

## Gestion des contraintes d'exploitation

L'automatisation devait tenir compte de la disponibilité des différents services utilisés.

Lors d'une période planifiée d'indisponibilité de l'infrastructure, la copie vers le stockage NFS a notamment été suspendue afin d'éviter des traitements inutiles ou en erreur.

Le fonctionnement normal a ensuite pu reprendre après le retour du service.

## Résultat

L'automatisation était terminée et utilisée en production au moment de mon départ.

L'utilisateur n'avait plus à :

- télécharger manuellement les différents fichiers ;
- les regrouper ;
- les compresser ;
- préparer l'archive.

Il lui suffisait désormais de récupérer l'archive automatiquement générée sur le stockage partagé et de la transmettre au service destinataire.

Cette automatisation a ainsi supprimé une grande partie des opérations manuelles répétitives réalisées auparavant.

## Documentation

Le fonctionnement de l'automatisation a été documenté afin de permettre :

- de comprendre les différentes étapes du traitement ;
- d'identifier le fonctionnement du script ;
- de faciliter son exploitation ;
- de permettre sa reprise par un autre administrateur en cas de besoin.

## Retour d'expérience

Ce projet m'a montré l'intérêt de partir du besoin réel de l'utilisateur plutôt que d'automatiser uniquement pour des raisons techniques.

La valeur du projet ne venait pas seulement du script Bash : elle résidait dans la suppression d'un ensemble de tâches manuelles répétitives tout en conservant de la visibilité sur le bon fonctionnement du traitement grâce à la supervision.

Avec davantage d'expérience, je renforcerais aujourd'hui cette solution avec :

- une gestion plus formalisée des erreurs à chaque étape ;
- des contrôles explicites de disponibilité des ressources externes ;
- une journalisation structurée ;
- des mécanismes de reprise automatique en cas d'échec ;
- des indicateurs permettant de mesurer le nombre de traitements réalisés et les éventuelles erreurs ;
- une alerte automatique en cas d'échec plutôt qu'une surveillance principalement basée sur la consultation de Nagios.

## Compétences mobilisées

### Gestion de projet technique

- Analyse d'un besoin utilisateur
- Proposition d'une solution
- Conception d'un processus automatisé
- Tests et validation utilisateur
- Mise en production
- Prise en compte des contraintes d'exploitation
- Documentation

### Techniques

- Linux
- Bash
- Cron
- NFS
- Nagios
- Scripting
- Supervision
- Gestion de fichiers et archives

### Transverses

- Autonomie
- Analyse du besoin
- Amélioration continue
- Collaboration avec un utilisateur
- Résolution de problèmes
- Documentation
