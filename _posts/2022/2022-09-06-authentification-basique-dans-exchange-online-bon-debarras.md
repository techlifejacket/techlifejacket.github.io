---
title: "Authentification basique dans Exchange Online : fin du game."
date: 2022-09-06 21:23:00:00 +02:00
layout: post
tags: [Office 365,exchange online,microsoft]
categories: [annonces]
readtime: true
comments: true
cover-img: "assets/img/banners/office-365-banner.png"
thumbnail-img: "assets/img/posts/2022/09/eol-logo.png"
---

**Le 1er septembre 2022, Microsoft a [mis en ligne un article](https://techcommunity.microsoft.com/t5/exchange-team-blog/basic-authentication-deprecation-in-exchange-online-september/ba-p/3609437) supplémentaire pour rappeler à ses clients que l'authentification basique (Basic Auth) commencera à être désactivée à compter du 1er octobre 2022. Les plateformes sélectionnées le seront de manière aléatoire** 

*ENFIN !* Microsoft force la main de ses utilisateurs et commencera à désactiver les protocoles *legacy* **à partir du 1er octobre**. D'après Microsoft, voici la situation actuelle *(ce texte est traduit depuis la source cité juste au dessus)* :

>*Nous reconnaissons que, malheureusement, de nombreux locataires ne sont toujours pas préparés à ce changement. Malgré plusieurs articles de blog, messages du centre de messagerie, interruptions de service et couverture via des tweets, des vidéos, des présentations de conférence et plus encore, certains clients ne sont toujours pas au courant de ce changement à venir. Il existe également de nombreux clients conscients du délai qui n'ont tout simplement pas effectué les travaux nécessaires pour éviter une panne.*
>
>*Notre objectif avec cet effort n'a jamais été que de protéger vos données et vos comptes contre le nombre croissant d'attaques que nous constatons et qui tirent parti de l'authentification de base.*
>
>*Cependant, nous comprenons que le courrier électronique est un service essentiel pour bon nombre de nos clients et que la désactivation de l'authentification de base pour beaucoup d'entre eux pourrait avoir un impact considérable.*

L'information va être diffusée de la manière suivante auprès des administrateurs : sept jours avant la désactivation de l'authentification basique sur une plateforme Office 365, un bandeau sera affiché dans le centre d'administration (comment ça, vous n'y allez jamais ?). La désactivation de l'authentification basique aura pour effet l'impossibilité d'utiliser un couple login / mot de passe sur les protocoles suivants :

- Offline Address Book (OAB)
- Exchange Web Services (EWS)
- MAPI
- RPC
- Remote Powershell
- Exchange ActiveSync (EAS)
- POP
- IMAP

Le SMTP AUTH n'est pour l'instant pas concerné (sinon, soyons honnêtes, on va faire tomber tous les scan-to-mail de la planète). 

Autre impact : il faudra obligatoirement utiliser Outlook 2013 Service Pack 1 pour se connecter aux services Microsoft 365 *(j'ai vu des packs Office 2010 en production il y a quelques mois)*.

# Le bug du 31 Décembre 2022

Soyons clairs : si vous ne vous êtes pas préparé à ce changement majeur, toutes mes condoléances. Plus sérieusement, la suppression de cette méthode d'authentification peut avoir beaucoup d'effets de bord mais il est possible de vérifier vos journaux de connexion Azure AD afin de vérifier qui utilise de l'authentification basique. 

Microsoft fournit également un outil de diagnostic que vous pouvez appeler depuis [ce lien](https://aka.ms/PillarEXOBasicAuth) ou en cliquant sur le bouton "Aide et Support" depuis le centre d'administration. Entrez en suite les mots : **Diag: Enable Basic Auth in EXO**

**Au risque de me répéter : prenez ce sujet au sérieux !**

Microsoft publie également ce schéma du processus de désactivation :

![Processus de désactivation de Basic Auth sur Office 365](/assets/img/posts/2022/09/BasicFin06.png)

# JOKER

Pour ceux qui se retrouveraient devant le fait accompli, Microsoft vous offre un joker unique. Une fois Basic Auth désactivé sur votre *tenant*, vous pourrez réactiver cette méthode d'authentification en quelques clics et ce jusqu'au 31 décembre 2022. Sachez tout de même qu'au **1er janvier 2023**, l'authentification basique sera **désactivée définitivement sans retour en arrière possible**.

# Tout ça pour quoi ?

C'est tout simplement une question élémentaire de sécurité : même si la connexion aux services de Microsoft 365 s'effectuent grâce à HTTPS, les identifiants de connexion au serveur sont transmis en clair par le service ou l'utilisateur essayent de se connecter. Cela vous rend vulnérable certaines attaques comme [T0830 Man in the Middle](https://attack.mitre.org/techniques/T0830/).

Pour migrer vos charges de travail et applications s'appuyant sur l'authentification basique, utilisez des jetons OAuth ayant une durée de vie limitée dans le temps. Ces jetons ont l'avantage de ne pas pouvoir être utilisés pour s'authentifier sur les services autres que ceux pour lesquels ils ont été générés initialement.

Si cela peut vous être utile, la [docuementation permettant de désactiver l'authentification basique se trouve ici](https://docs.microsoft.com/en-us/exchange/clients-and-mobile-in-exchange-online/disable-basic-authentication-in-exchange-online?WT.mc_id=AZ-MVP-5004580). Bon courage :-)