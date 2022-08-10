---
title: "Solution à l'erreur : Start-ADSyncSyncCycle : Retrieving the COM class factory for remote component with CLSID {835BEE60-8731-4159-8BFF-941301D76D05}"
date: 2022-08-10 16:45:00:00 +01:00
layout: post
tags: [m365,azure ad connect, azure]
categories: azure-ad
readtime: true
comments: true
cover-img: "assets/img/banners/aadconnect-arch.png"
thumbnail-img: "assets/img/posts/2022/08/azure-active-directory.png"
---

Lors de l'exécution de la commande Powershell *Start-ADSyncSyncCycle*, un administrateur avec des privilèges limités peut rencontrer l'erreur suivante :

**Start-ADSyncSyncCycle : Retrieving the COM class factory for remote component with CLSID {835BEE60-8731-4159-8BFF-941301D76D05} from machine failed due to the following error: 80070005**

![Start-ADSyncSyncCycle error: 80070005](/assets/img/posts/2022/08/start-adsyncsynccyle-0x80070005.png)

Pour lancer une synchronisation Azure AD, l'administrateur doit être membre du groupe *ADSyncOperators*. Les utilisateurs intégrés à ce groupe ont accès aux opérations de synchonisation *Azure AD Connect* et peuvent :
- Exécuter une synchonisation totale ou partielle
- Afficher les statistiques de chaque synchronisation
- Enregistrer l'historique d'exécution dans un fichier

La synchronisation avec Azure s'exécute de manière planifiée. Toutefois, il peut être nécessaire d'exécuter l'applet de commande Start-ADSyncSyncCycle manuellement si vous avez créé un utilisateur ou modifié l'appartenance à un groupe et que vous souhaitez refléter immédiatement cette modification dans Azure AD.

Voici un simple script Powershell pour synchroniser Active Directory avec Azure AD à distance depuis un serveur de gestion. Ce script permet aux utilisateurs disposant de privilèges administratifs limités (Techniciens Helpdesk ou Administrateurs d'applications) de forcer une synchronisation des utilisateurs et des groupes.

```powershell
#Exécuter une synchro AzureAD Sync. S'il fonctionne avec succès, cela prendra environ 30 secondes. Si la fenêtre disparaît immédiatement, la commande a échoué et connectez-vous au serveur.
$aadsyncserver = "votre_serveur_ad_connect" #par exemple win-azuread.mondomaine.local
invoke-command -ComputerName $aadsyncserver -ScriptBlock {start-adsyncsynccycle} -ErrorAction Stop
Write-Host "L'Active Directory est en cours de synchronisation avec Azure AD. Cela prendra environ 30 secondes."
```

Pour démarrer ce script à distance, l'utilisateur doit être membre des groupes suivants :
- **Remote Management Users**
- **ADSyncOperators**

Si l'utilisateur n'est pas membre du groupe **Remote Management Users** il obtiendra le message suivant : 
**Connecting to remote server failed with the following error message : Access is denied. For more information, see the about_Remote_Troubleshooting Help topic.**

![Start-ADSyncSyncCycle error: 80070005](/assets/img/posts/2022/08/start-adsyncsynccyle-remote-failed.png)
