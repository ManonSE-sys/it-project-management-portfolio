# Refonte de la stratégie de sauvegarde

## Contexte

L'infrastructure disposait de deux mécanismes complémentaires de sauvegarde :

- BackupPC pour la sauvegarde de fichiers sur les serveurs ;
- les mécanismes de sauvegarde intégrés à Proxmox pour les machines virtuelles.

Un état des lieux a mis en évidence plusieurs problèmes dans l'organisation existante.

Les sauvegardes BackupPC prenaient plus de temps que prévu et pouvaient encore être en cours lorsque d'autres traitements de sauvegarde démarraient.

Nous avons également constaté que les sauvegardes BackupPC et Proxmox étaient planifiées sur des plages horaires similaires.

Cette situation était d'autant plus problématique que BackupPC pouvait sauvegarder certains fichiers correspondant eux-mêmes à des sauvegardes de machines virtuelles présentes sur les hôtes Proxmox.

Avec mon collègue et le responsable système côté client, nous avons décidé de revoir l'organisation globale des sauvegardes.

## Objectif

L'objectif était de restructurer la stratégie de sauvegarde afin de :

- éviter les chevauchements inutiles entre les différents mécanismes ;
- différencier les politiques de sauvegarde selon la criticité des serveurs ;
- adapter les fréquences et les durées de rétention ;
- éviter la sauvegarde inutile de données déjà protégées par un autre mécanisme ;
- réduire la durée des traitements BackupPC ;
- faciliter le suivi et la maintenance des configurations.

## Mon rôle

J'ai participé à l'analyse de l'existant puis pris en charge une grande partie de la mise en œuvre de la nouvelle organisation.

Mes activités comprenaient notamment :

- l'inventaire des sauvegardes existantes ;
- l'analyse des fréquences et des horaires ;
- l'identification des serveurs concernés ;
- l'analyse des exclusions existantes ;
- la définition de nouveaux profils de sauvegarde ;
- l'adaptation des fréquences et des politiques de rétention ;
- la modification des sauvegardes Proxmox ;
- la modification des profils BackupPC déployés via Puppet ;
- la validation des répertoires à sauvegarder avec les interlocuteurs concernés ;
- le suivi de la migration ;
- la vérification du bon fonctionnement des sauvegardes ;
- la documentation de la nouvelle organisation.

## Analyse de l'existant

La première étape a consisté à réaliser un état des lieux des deux systèmes de sauvegarde.

J'ai notamment recensé :

- les serveurs sauvegardés ;
- les mécanismes utilisés ;
- les fréquences de sauvegarde ;
- les horaires d'exécution ;
- les politiques de rétention ;
- les exclusions existantes.

Cette analyse a permis de mettre en évidence des chevauchements entre les sauvegardes BackupPC et Proxmox.

Certains traitements BackupPC récupéraient également des fichiers correspondant à des sauvegardes de machines virtuelles, alors que celles-ci étaient déjà protégées par le mécanisme Proxmox.

Ces traitements augmentaient inutilement la durée des sauvegardes.

## Définition des nouveaux profils

De nouveaux profils de sauvegarde ont été définis en fonction de la criticité et du rôle des serveurs.

Les différents profils pouvaient ainsi disposer :

- de fréquences différentes ;
- de politiques de rétention différentes ;
- d'exclusions adaptées aux données réellement nécessaires.

Pour les serveurs utilisés par d'autres équipes ou hébergeant des applications spécifiques, je faisais confirmer les répertoires à sauvegarder afin d'éviter d'exclure une donnée nécessaire à une restauration.

## Refonte des sauvegardes BackupPC

Les profils BackupPC étaient déployés sur les serveurs via Puppet.

J'ai adapté les profils puis migré progressivement les serveurs vers la nouvelle configuration.

La migration était réalisée serveur par serveur.

J'ai commencé par des serveurs peu critiques afin de valider le fonctionnement des nouveaux profils avant d'étendre leur utilisation.

Les anciens profils ont été conservés pendant la transition afin de pouvoir revenir rapidement à la configuration précédente en cas de problème.

## Refonte des sauvegardes Proxmox

Les sauvegardes des machines virtuelles ont également été réorganisées.

Les modifications ont été appliquées progressivement par groupes de serveurs.

Cette nouvelle organisation permettait notamment de mieux répartir les périodes de sauvegarde et d'éviter certains chevauchements avec BackupPC.

## Validation

Après chaque modification, je vérifiais le bon fonctionnement des sauvegardes à partir :

- des statuts disponibles dans BackupPC ;
- de la supervision existante dans Nagios ;
- des résultats des traitements de sauvegarde.

Aucun incident significatif n'a été rencontré pendant la migration.

Les sauvegardes BackupPC sont également devenues moins longues après la refonte.

## Suivi du projet

J'utilisais un fichier Excel afin de suivre l'avancement de la migration.

Ce suivi permettait notamment d'identifier :

- les serveurs analysés ;
- les profils définis ;
- les serveurs déjà migrés ;
- les serveurs restant à traiter ;
- l'état général de la migration.

## Documentation

La nouvelle organisation et les configurations associées ont été documentées afin de faciliter :

- la compréhension des différentes politiques de sauvegarde ;
- l'exploitation quotidienne ;
- l'intégration de nouveaux serveurs ;
- la reprise du sujet par un autre administrateur.

## Résultat

Le projet était terminé avant mon départ.

La refonte a permis :

- de disposer de politiques de sauvegarde adaptées à la criticité des serveurs ;
- de mieux répartir les différents traitements ;
- de limiter les sauvegardes redondantes ;
- de réduire la durée de certains traitements BackupPC ;
- de rendre l'organisation générale plus lisible et maintenable.

## Retour d'expérience

Ce projet m'a permis de comprendre qu'une stratégie de sauvegarde ne se limite pas à vérifier qu'un outil exécute correctement ses tâches.

Il faut également prendre en compte :

- les interactions entre plusieurs mécanismes de sauvegarde ;
- les horaires d'exécution ;
- la volumétrie ;
- la criticité des systèmes ;
- les politiques de rétention ;
- les exclusions ;
- les besoins réels de restauration.

Avec davantage d'expérience, j'ajouterais aujourd'hui une étape importante à ce type de projet : des tests de restauration formalisés.

Le bon déroulement d'une sauvegarde ne garantit pas à lui seul que la donnée pourra être restaurée dans les conditions attendues.

Je définirais donc également :

- des scénarios de restauration ;
- une fréquence de tests ;
- des critères de validation ;
- un suivi des temps de restauration ;
- une procédure documentée de restauration.

## Compétences mobilisées

### Gestion de projet technique

- Analyse de l'existant
- Définition d'une nouvelle organisation
- Priorisation selon la criticité
- Migration progressive
- Gestion du risque
- Suivi d'avancement
- Validation
- Documentation
- Coordination avec les utilisateurs des systèmes

### Techniques

- Linux
- BackupPC
- Proxmox
- Puppet
- Nagios
- Sauvegarde et restauration
- Gestion de la rétention
- Gestion de profils de sauvegarde
- Virtualisation

### Transverses

- Analyse
- Autonomie
- Organisation
- Amélioration continue
- Communication avec des interlocuteurs techniques
- Documentation
