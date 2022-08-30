---
title: "Implémenter DMARC (avec ou sans Office 365)"
date: 2022-08-30 21:39:00:00 +02:00
layout: post
tags: [m365,dmarc,authentification,spam]
categories: [dmarc]
readtime: true
comments: true
cover-img: "assets/img/banners/email-authentication.png"
thumbnail-img: "assets/img/posts/2022/08/email-authentication-thumb.png"
---

Tout administrateur de services de messagerie devrait implémenter le protocole **DMARC** qui veut dire *Domain-based Message Authentication, Reporting and Conformance*. Ce protocole s'appuie sur DKIM et SPF (on aura l'occasion d'en reparler). La mise en oeuvre de ces trois protocoles permet d'authentifier les courriels et d'obtenir des rapports à des fins d'analyse.

# Réfléchissez avant de cliquer
DMARC est utilisé pour lutter notamment contre le *phishing* (*hameçonnage* en français). Ces attaques sont probablement les plus répandues sur Internet : elles sont faciles à mettre en oeuvre et donnent de très bons résultats grâce à [Madame Michu](https://fr.wiktionary.org/wiki/Madame_Michu). Le but de ces attaques ? Récupérer du fric et des données (et donc encore plus de fric) par tous les moyens : fausses factures, arnaque au président, ransomware, ... 

On ne le répétera jamais assez : **réfléchissez avant de cliquer** !

# DMARC, agit-il sur le courrier entrant ou sortant ?

Pour être clair et concis : **DMARC agit sur le courrier sortant**.

La confusion vient souvent d'explications bancales. J'ai moi-même mis du temps à le comprendre, une politique DMARC n'aura pas d'effet sur le volume de SPAM reçu. En revanche, elle sera redoutable sur les tentatives d'usurpation de vos domaines. 

Une politique stricte fonctionne de la manière suivante : vous utilisez DKIM pour signer les courriels sortants et vous publiez un enregistrement SPF avec une liste de serveurs d’envoi légitimes. Cela permet au serveur destinataire de valider que le courrier n’a pas été modifié et qu’il a été effectivement envoyé à partir d’un serveur de messagerie appartenant à votre entreprise. En plus de cela, vous utilisez DMARC pour informer le destinataire sur la manière de gérer les échecs de validation DKIM et SPF et où envoyer un rapport d'échec lors de la validation.

DMARC ne vous protègera pas contre la réception de courriels frauduleux ou de phishing n'usurpant pas vos domaines. Mettez en place une protection complémentaire sur vos serveurs de messagerie, plateforme Office 365 ou Google Workspace. 

*Information intéressante pour les administrateurs de plateformes Office 365 : une politique DMARC stricte ne vous protègera pas totalement en raison de la politique de Microsoft relative aux "Safe Senders". Je vous renvoie vers le [post LinkedIn de Christophe DARY](https://www.linkedin.com/posts/christophe-dary-85330561_mitiga-phishing-microsoft-activity-6970377905944068097-tnKW?utm_source=share&utm_medium=member_desktop) pour plus d'infos.*

# Le processus de traitement DMARC illustré

Voici le processus exécuté du côté du destinataire :

![Processus de traitement DMARC](/assets/img/posts/2022/08/processus-anayse-dmarc.png)

Lors de la réception d'un courriel, l'implémentation du protocole est vérifiée dans les enregistrements DNS de l'expéditeur : on recherche la présence d'un enregistrement TXT du type *_dmarc@entreprise.fr*.

Si un enregistrement DMARC valide est trouvé, le destinataire sait désormais comment traiter le courriel : s'il échoue à la validation DKIM et/ou SPF, le courriel pourra alors être rejeté ou mis en quarantaine. On ne laisse pas une **politique DMARC** *p=none* en place sauf lors de la phase d'audit (voir Partie 2).

# Mise en oeuvre d'une politique DMARC

Dnas le prochain article concernant DMARC, nous verrons comment configurer l'enregistrement DMARC et comment mettre en oeuvre une politique DMARC.

## Liste des articles relatifs à DMARC
1. [Implémenter DMARC (avec ou sans Office 365)](https://techlifejacket.github.io/dmarc/implementer-dmarc-avec-ou-sans-office-365)