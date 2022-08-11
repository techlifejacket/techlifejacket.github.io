---
title: "Microsoft 365 - Protection des données, sauvegarde et délais de rétention"
date: 2022-08-11 09:34:00:00 +01:00
layout: post
tags: [m365,sauvegarde,conformité]
categories: Microsoft 365
readtime: true
comments: true
cover-img: "assets/img/banners/office-365-banner.png"
thumbnail-img: "assets/img/posts/2022/08/microsoft-365-thumb.png"
---

Les services Microsoft 365 sont généralement géo-redondants : les données sont stockées dans au moins deux datacenter.

Cassons le mythe tout de suite : **Microsoft ne sauvegarde pas les données de ses clients** mais fournit juste des outils permettant la rétention et la récupération des éléments supprimés. Microsoft assure la haute disponibilité des données, **le client final reste responsable de ses données**. Cela étant dit, la nécessité d'utiliser un système de sauvegarde devient évidente.

![Microsoft 365 data backup](/assets/img/posts/2022/08/m365-data-backup.png)

# Délais de rétention et récupération

## Comptes Microsoft 365

Lorsqu'un utilisateur est supprimé, l'administrateur dispose de 30 jours pour le restaurer ou récupérer ses données (courriels, OneDrive, conversation Teams)
Exchange
Lorsqu'un utilisateur supprime un courriel, il est déplacé dans le dossier éléments supprimés. Si le dossier est vidé, les éléments définitivement supprimés sont encore récupérables pendant une durée fixée à 14 jours par défaut. Ce délai peut être augmenté jusqu'à une durée de 30 jours au maximum.

A noter, un compte placé en conservation pour litige ('onHold') n'est pas supprimé.
Sharepoint
Dans SharePoint Online, les éléments sont conservés pendant 93 jours à partir du moment où ils sont supprimés de leur emplacement d’origine.
Seuls les administrateurs de site peuvent les supprimer et les restaurer.

## Listes et Bibliothèques SharePoint
Lors de la suppression d'une collection de sites, la hiérarchie des sites de la collection et tout le contenu qu’elle contient sont également supprimés :

- les documents et bibliothèques de documents ;
- Listes et données de liste
- Paramètres de configuration de site
- Informations de rôle et de sécurité relatives au site ou à ses sous-sites
- Sous-sites du site web de niveau supérieur, leur contenu et les informations utilisateur

Les collections de sites supprimées sont **conservées pendant 93 jours**. Après 93 jours, *les sites et tous leurs contenus et paramètres sont supprimés définitivement*, y compris les listes, bibliothèques, pages et tous les sous-sites.

## Microsoft Teams

### Equipe Teams

Une équipe Teams est composée de plusieurs objets : un groupe Office 365, une boite Exchange et un site SharePoint.

En cas de suppression d’une équipe, le groupe Office 365 est supprimé, le site SharePoint et les publications aussi. Les éléments sont récupérables durant 30 jours sauf pour les fichiers où c'est la rétention Sharepoint qui s'applique (93 jours).

### Conversation Teams

Les conversations peuvent être partiellement restaurées, mais les fichiers sont dans les OneDrive individuels donc non maitrisés.

Les conversations doivent être considérées comme éphémères. S'il y a besoin de suivi, de sécurité et de protection des contenus, il faut créer une équipe.

### Wiki Teams

Un Wiki est composé de fichiers (les pages) stockés dans une Bibliothèque SharePoint dans le site associé. C'est la rétention Sharepoint qui s'applique (93 jours).

## Autres objets Microsoft 365
- Planner, To Do, etc. : pas de réelle conservation des données
- OneNote : cela dépend d'où est stocké le carnet de notes

## Gestion des stratégies de rétention

Les stratégies de rétention peuvent être gérées dans [Microsoft Purview](https://compliance.microsoft.com/)

![Microsoft 365 data backup](/assets/img/posts/2022/08/purview-retention-strategy.png)
