# Centralisation des logs avec Graylog

## Contexte

L'entreprise ne disposait pas encore de solution centralisée pour collecter et consulter les journaux de ses serveurs.

Dans une logique d'amélioration de la sécurité et avec la perspective de disposer à terme d'une approche de type SIEM, il a été décidé de mettre en place une première centralisation des logs avec Graylog.

La solution Graylog avait été choisie en amont par le responsable de l'équipe Infrastructure & Cybersecurity.

Le périmètre cible concernait plusieurs centaines de serveurs Windows et Linux.

## Objectif

Mettre en place une plateforme centralisée permettant de :

* collecter les journaux des serveurs Linux et Windows ;
* faciliter leur consultation et leur recherche ;
* enrichir la journalisation Windows ;
* améliorer la visibilité sur les événements de sécurité ;
* préparer une évolution ultérieure vers une démarche de type SIEM.

## Mon rôle

Le projet m'a été confié par le responsable de l'équipe Infrastructure & Cybersecurity.

La solution ayant déjà été choisie, j'étais principalement chargée de sa mise en œuvre technique et du déploiement progressif de la collecte des logs.

Je travaillais de manière largement autonome sur le projet.

Mes activités comprenaient notamment :

* l'installation et la configuration de la plateforme Graylog ;
* la configuration de la collecte des logs Linux ;
* la préparation de la collecte des logs Windows ;
* la préparation du package et de la configuration NxLog ;
* l'intégration des serveurs Windows aux collections SCCM ;
* la mise en place d'une GPO permettant d'enrichir la journalisation Windows ;
* la création de recherches, tableaux de bord ou visualisations dans Graylog ;
* la résolution des problèmes rencontrés pendant le déploiement.

## Parties prenantes

Les principaux interlocuteurs étaient :

* le responsable de l'équipe Infrastructure & Cybersecurity ;
* l'administrateur SCCM.

La préparation du package et de la configuration NxLog était réalisée de mon côté.

L'administrateur SCCM assurait la partie déploiement dans SCCM. Une fois les collections créées, je pouvais ensuite ajouter les serveurs concernés afin de poursuivre progressivement le déploiement.

## Stratégie de déploiement

J'ai choisi de commencer par les serveurs Linux, car leur intégration était plus simple.

Le périmètre Linux concernait une dizaine de serveurs.

La configuration de la remontée des logs était réalisée directement dans `rsyslog` et a été effectuée manuellement compte tenu du faible nombre de machines.

Une fois le périmètre Linux terminé, le projet s'est poursuivi sur les serveurs Windows.

Le déploiement Windows devait être réalisé progressivement, en commençant par les serveurs les moins critiques avant d'étendre la collecte à d'autres catégories de serveurs.

## Collecte des logs Linux

La remontée des événements Linux reposait sur `rsyslog`.

Chaque serveur était configuré afin d'envoyer ses journaux vers Graylog.

Compte tenu du nombre limité de serveurs Linux concernés, la configuration a été réalisée manuellement plutôt que par automatisation.

Le périmètre Linux avait été entièrement intégré avant la fin de mon alternance.

## Collecte des logs Windows

Pour les serveurs Windows, la collecte reposait sur NxLog.

J'étais chargée de préparer :

* le package ;
* la configuration de l'agent ;
* les paramètres nécessaires à la remontée des logs.

L'administrateur SCCM assurait ensuite le déploiement technique du package.

Je pouvais ensuite ajouter progressivement les serveurs aux collections SCCM prévues pour le déploiement.

Le projet a commencé par des serveurs moins critiques avant d'être progressivement étendu à d'autres catégories de machines.

Au moment de mon départ, une partie du parc Windows avait été intégrée.

## Enrichissement de la journalisation Windows

À la suite d'un audit de sécurité, il avait été demandé d'activer des événements Windows supplémentaires afin d'améliorer la visibilité sur certaines activités.

J'ai créé une GPO permettant d'enrichir la journalisation des serveurs Windows.

Les événements concernés avaient été définis à partir des recommandations de l'audit.

## Exploitation des données dans Graylog

J'ai également commencé à créer des éléments permettant d'exploiter plus facilement les données remontées dans Graylog.

J'avais notamment mis en place des recherches ou visualisations concernant les échecs d'authentification (`failed logons`).

D'autres tableaux de bord ou recherches avaient également été construits, même si je ne dispose plus aujourd'hui du détail exact de leur contenu.

## Difficultés rencontrées

### Gestion du stockage et de la rétention

L'une des principales difficultés concernait le stockage utilisé par Graylog.

Au cours du projet, nous avons constaté que la gestion de la rétention des logs nécessitait une attention particulière, notamment dans le contexte de la version utilisée.

Cela a entraîné des problématiques de croissance du stockage qu'il a fallu corriger au cours du projet.

Je ne dispose plus aujourd'hui du détail exact de la solution appliquée, mais cet incident m'a permis de prendre conscience de l'importance de définir dès le début :

* la durée de rétention ;
* le volume de logs attendu ;
* les mécanismes de rotation ;
* la capacité de stockage nécessaire.

### Problème de remontée d'un agent

Lors du déploiement, un agent ne remontait pas correctement ses données vers Graylog.

Le problème a été diagnostiqué et corrigé au cours du projet.

Je ne dispose plus du détail technique exact de la résolution.

### Configuration des alertes e-mail

J'ai également commencé à expérimenter les fonctions d'alerting de Graylog.

Une première configuration d'alertes e-mail a généré un volume beaucoup trop important de notifications.

Le nombre de messages reçus a fini par provoquer le blocage temporaire de mon adresse e-mail.

Cet incident m'a montré la nécessité de définir précisément les conditions de déclenchement des alertes avant leur mise en production afin d'éviter les faux positifs et les volumes excessifs de notifications.

## Suivi du projet

Le projet étant principalement réalisé par moi-même, il n'y avait pas de dispositif de suivi formel avec un tableau de pilotage dédié.

L'avancement se faisait progressivement en fonction des serveurs intégrés et des problèmes rencontrés.

Des échanges avec mon responsable avaient lieu lors de réunions ou par e-mail lorsque cela était nécessaire.

## État du projet à mon départ

Au moment de la fin de mon alternance :

* la plateforme Graylog était opérationnelle ;
* la collecte des logs Linux était terminée ;
* la collecte Windows avait commencé ;
* une partie du parc Windows était intégrée ;
* la journalisation Windows avait été enrichie via GPO ;
* des premières recherches, visualisations et alertes avaient été testées.

Le déploiement sur l'ensemble du parc Windows n'était pas encore terminé.

## Retour d'expérience

Ce projet m'a permis de comprendre qu'un projet de centralisation des logs ne se limite pas au déploiement d'un outil.

Plusieurs éléments doivent être pensés dès le début :

* la volumétrie ;
* le stockage ;
* la durée de rétention ;
* les sources de logs réellement utiles ;
* les événements de sécurité à collecter ;
* les critères de déclenchement des alertes ;
* l'ordre de déploiement ;
* la validation du bon fonctionnement des agents.

Avec davantage d'expérience, je commencerais aujourd'hui ce type de projet par une phase de cadrage plus structurée.

Je chercherais notamment à définir :

* les objectifs de sécurité précis ;
* le périmètre cible ;
* les sources de logs prioritaires ;
* les besoins de stockage ;
* la politique de rétention ;
* les indicateurs de réussite ;
* les cas d'usage de détection recherchés ;
* une stratégie de déploiement par vagues ;
* les règles d'alerting avant leur activation en production.

Je prévoirais également une phase pilote permettant de mesurer la volumétrie réelle avant d'étendre la collecte à plusieurs centaines de serveurs.

## Compétences mobilisées

### Gestion de projet

* Prise en charge autonome d'un projet technique
* Déploiement progressif
* Priorisation par criticité
* Coordination avec un expert SCCM
* Gestion d'incidents
* Adaptation face aux difficultés rencontrées
* Retour d'expérience

### Cybersécurité

* Centralisation de logs
* Journalisation de sécurité
* Analyse d'événements
* Failed logons
* Alerting
* Préparation d'une démarche de type SIEM
* Prise en compte de recommandations d'audit

### Techniques

* Graylog
* CentOS
* Linux
* rsyslog
* Windows Server
* NxLog
* SCCM
* GPO
* Active Directory

### Transverses

* Autonomie
* Résolution de problèmes
* Collaboration avec des experts techniques
* Analyse
* Documentation
