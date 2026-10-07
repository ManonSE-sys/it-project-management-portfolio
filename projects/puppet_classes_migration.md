# Refonte et migration des classes Puppet

## Contexte

L'infrastructure était administrée en partie à l'aide de Puppet.

Le modèle de configuration existant reposait sur des classes très générales : un grand nombre de paramètres étaient appliqués par défaut à l'ensemble des serveurs, puis certaines configurations étaient désactivées lorsqu'elles ne devaient pas s'appliquer.

Cette organisation rendait les fichiers Puppet particulièrement volumineux et difficiles à maintenir. Certains fichiers pouvaient contenir plusieurs milliers de lignes.

Les responsables techniques souhaitaient évoluer vers une logique inverse : partir d'une configuration minimale, puis ajouter uniquement les paramètres réellement nécessaires en fonction du rôle de chaque serveur.

Le périmètre cible concernait l'ensemble du parc, soit environ 120 serveurs Linux.

## Objectif

Refondre l'organisation des classes Puppet afin de disposer d'une configuration :

- plus lisible ;
- plus modulaire ;
- plus facile à maintenir ;
- adaptée aux différents rôles des serveurs ;
- permettant d'intégrer progressivement l'ensemble du parc dans Puppet.

L'objectif était également de réduire la complexité des classes existantes en remplaçant une logique de configuration globale par plusieurs classes adaptées aux différents types de serveurs.

## Mon rôle

J'ai pris en charge la conception et la mise en œuvre de cette nouvelle organisation Puppet.

Mes responsabilités comprenaient notamment :

- l'analyse des classes existantes ;
- l'identification de plusieurs catégories de serveurs ;
- la définition de la nouvelle organisation des classes ;
- la création des nouvelles classes Puppet ;
- l'intégration des configurations nécessaires à chaque type de serveur ;
- le rattachement progressif des serveurs aux nouvelles classes ;
- les tests après migration ;
- le suivi de l'avancement ;
- le reporting auprès du responsable technique côté client.

## Refonte de l'organisation Puppet

L'ancien modèle appliquait un ensemble important de configurations par défaut à l'ensemble des serveurs, puis utilisait des exceptions lorsqu'un serveur devait fonctionner différemment.

J'ai choisi de structurer les nouvelles classes selon les différents rôles de serveurs identifiés.

Chaque type de serveur disposait ainsi d'une classe contenant uniquement les configurations nécessaires à son fonctionnement.

Cette nouvelle organisation permettait de réduire fortement la taille et la complexité des fichiers Puppet.

Des fichiers pouvant auparavant contenir plusieurs milliers de lignes ont ainsi été remplacés par des classes plus ciblées, généralement de quelques centaines de lignes.

## Migration des serveurs

La migration a été réalisée progressivement.

J'ai commencé par des serveurs peu critiques afin de valider le fonctionnement des nouvelles classes avant d'étendre leur utilisation.

Les serveurs étaient ensuite migrés individuellement.

Pour chaque serveur :

1. le serveur était rattaché à la nouvelle classe correspondant à son rôle ;
2. l'agent Puppet était exécuté manuellement ;
3. les changements appliqués étaient contrôlés directement pendant l'exécution ;
4. le bon fonctionnement des services était vérifié ;
5. Nagios était consulté afin de vérifier l'état général du serveur ;
6. des tests applicatifs étaient réalisés lorsque cela était nécessaire.

Cette approche progressive permettait de limiter les risques avant d'étendre la migration au reste du parc.

## Gestion du risque et retour arrière

La migration a été réalisée de manière prudente afin d'éviter les interruptions de service.

Les anciennes classes Puppet ont été conservées pendant la transition.

En cas de problème, il était donc possible de rattacher de nouveau un serveur à son ancienne configuration.

Des sauvegardes étaient également disponibles afin de faciliter une restauration si nécessaire.

Cette stratégie permettait de disposer d'une solution de retour arrière pendant les différentes phases de migration.

## Versioning avec Git

Les fichiers Puppet étaient versionnés avec Git.

Cette organisation permettait de conserver l'historique des modifications apportées aux classes et de suivre les évolutions de la configuration.

Git était déjà présent dans l'environnement lorsque j'ai pris en charge le projet. J'ai été accompagnée lors de mes premières utilisations avant de l'intégrer à mon travail quotidien sur les configurations Puppet.

## Suivi de l'avancement

J'utilisais un fichier Excel afin de suivre l'état de la migration des différents serveurs.

Ce suivi permettait notamment d'identifier :

- les serveurs déjà migrés ;
- les serveurs restant à traiter ;
- leur état d'intégration dans Puppet.

Il me permettait également de communiquer l'avancement du projet au responsable technique côté client lorsqu'il en faisait la demande.

## Difficultés rencontrées

La principale difficulté du projet concernait la conception des nouvelles classes.

Avant ce projet, j'avais principalement travaillé sur l'existant :

- ajout de nouveaux serveurs ;
- modification de configurations existantes ;
- création de classes simples pour certains besoins spécifiques, notamment NTP ou NFS.

La refonte m'a demandé d'aller plus loin en définissant moi-même une nouvelle organisation cohérente pour plusieurs types de serveurs.

Cela nécessitait de bien comprendre :

- les configurations existantes ;
- les différences entre les rôles des serveurs ;
- les paramètres réellement communs ;
- les éléments devant rester spécifiques.

La migration elle-même n'a pas provoqué d'incident significatif, notamment grâce au déploiement progressif et aux vérifications réalisées après chaque modification.

## Résultat

Le projet a été terminé avant mon départ.

La nouvelle organisation Puppet permettait de disposer de classes :

- plus ciblées ;
- plus lisibles ;
- plus simples à maintenir ;
- mieux adaptées aux différents rôles des serveurs.

La migration du parc concerné vers cette nouvelle organisation a également été menée à son terme.

Cette refonte a permis de réduire la complexité de la gestion des configurations tout en facilitant l'intégration de nouveaux serveurs dans Puppet.

## Retour d'expérience

Ce projet m'a permis de passer d'une utilisation principalement opérationnelle de Puppet à une réflexion plus globale sur l'organisation et la maintenabilité d'une infrastructure as code.

J'ai notamment appris qu'une configuration fonctionnelle n'est pas nécessairement une configuration facile à maintenir.

Avec davantage d'expérience, je formaliserais aujourd'hui davantage la phase de conception avant la migration, notamment avec :

- une cartographie des différents rôles de serveurs ;
- une définition formelle des configurations communes et spécifiques ;
- des critères de validation définis avant chaque migration ;
- un suivi des risques ;
- une procédure de retour arrière documentée ;
- éventuellement davantage de tests automatisés avant application en production.

Je conserverais en revanche l'approche progressive utilisée pendant le projet, avec une migration initiale sur des serveurs peu critiques avant généralisation.

## Compétences mobilisées

### Gestion de projet technique

- Analyse de l'existant
- Conception d'une nouvelle organisation
- Planification d'une migration progressive
- Priorisation selon la criticité
- Suivi d'avancement
- Gestion du risque
- Stratégie de retour arrière
- Reporting
- Validation après changement

### Techniques

- Linux
- Puppet
- Infrastructure as Code
- Git
- Nagios
- NTP
- NFS
- Gestion de configurations
- Tests de services

### Transverses

- Autonomie
- Analyse
- Structuration
- Résolution de problèmes
- Amélioration de la maintenabilité
- Communication avec des interlocuteurs techniques
