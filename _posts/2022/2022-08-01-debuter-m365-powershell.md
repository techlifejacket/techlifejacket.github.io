---
title: "Débuter avec Powershell pour Microsoft 365"
date: 2022-08-01 22:00:00:00 +01:00
layout: post
tags: [m365,powershell]
categories: tuto
readtime: true
comments: true
cover-img: "assets/img/banners/powershell-banner.jpg"
thumbnail-img: "assets/img/posts/2022/08/365-ps.png"
---

# Comment se connecter à Office 365 et Exchange Online via Powershell ?

PowerShell est un excellent moyen de gérer votre environnement Office 365. Il vous permet d’automatiser de nombreuses tâches en écrivant vos propres scripts ou en modifiant les paramètres avec une seule commande. La première étape consiste à connecter PowerShell à Office 365.

Il existe deux façons de se connecter à Office 365 dans PowerShell : via le Module Microsoft Azure Active Directory pour Windows Powershell (*MSOnline*) ou via le nouveau module Azure Active Directory PowerShell pour Graph (*AzureAD*). Pour vous connecter à Exchange Online, il ne vous faudra qu'un seul module supplémentaire.

Vous aurez besoin d'installer les deux modules *MSOnline* et *AzureAD* car toutes les commandes ne sont pas encore disponibles dans le module *AzureAd*.

## Installation des modules Powershell

Tout d’abord, installeons les deux modules PowerShell. Vous pouvez les utiliser ensemble sur votre système sans aucun problème.

### Installer le module AzureAd dans Powershell

Ouvrez PowerShell en mode administrateur (*Touche Windows + X* et sélectionnez Windows PowerShell (Admin))
Tapez la commande suivante : 

```powershell
Install-Module AzureAD
```

### Installer le module MSOnline

```powershell
Install-Module MSOnline
```

### Installer le module Exchange Online Management

```powershell
Install-Module ExchangeOnlineManagement
```

## Connexion à Office 365 via Powershell

Nos deux modules sont maintenant installés, nous pouvons donc nous connecter à Office 365 depuis la console PowerShell. 

Pour vous connecter au service MSOnline, vous devez exécuter la commande suivante, cela vous ouvrira une fenêtre de connexion moderne à Office 365 afin de valider vos identiaints ainsi que le MFA.

```powershell
Connect-MSolService
```

Vous pouvez maintenant utiliser les applets de commande MSol dans PowerShell, vous trouverez une vue d’ensemble de ces applets de commande dans la [documentation Microsoft](https://docs.microsoft.com/en-us/powershell/module/msonline/?view=azureadps-1.0).

## Connexion via le module AzureAD

C'est cette commande qui vous permettra de vous connecter à MSGraph API via le module Powershell AzureAD.

```powershell
Connect-AzureAD
```
## Connexion à Exchange Online Management

Pour vous connecter à Exchange Online, utilisez la commande suivante 

```powershell
Connect-ExchangeOnline -UserPrincipalName <UPN> [-ShowBanner:$false] [-ExchangeEnvironmentName <Value>] [-DelegatedOrganization <String>] [-PSSessionOption $ProxyOptions]
```
Exemple : 

```powershell
Connect-ExchangeOnline -UserPrincipalName admin@domain.com 
```
Si vous avez un accès délégué à un autre tenant (très utile pour les MSP), utilisez plutôt la commande suivante :

```powershell
Connect-ExchangeOnline -UserPrincipalName admin@domain.com -DelegatedOrganization contoso.onmicrosoft.com
```

Dans les prochains tutos, nous verrons quelques commandes utiles au quotidien pour la gestion des plateformes Office 365 via Powershell. 