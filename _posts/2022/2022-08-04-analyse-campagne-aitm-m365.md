---
title: "Campagne AiTM ciblant les utilisateurs Microsoft 365"
date: 2022-08-04 22:00:00:00 +01:00
layout: post
tags: [m365,AiTM,phishing,MFA,spoofing]
categories: cybersécurité
readtime: true
comments: true
cover-img: "assets/img/banners/cybersec.jpeg"
thumbnail-img: "assets/img/posts/2022/08/cybersec.png"
---

Une campagne utilisant des techniques *adversary-in-the-middle (AiTM)* (voir [T1557](https://attack.mitre.org/techniques/T1557) pour plus d'infos) associées à des techniques d'évasion diverses cible les utilisateurs de plateformes Office 365. Cette technique d'attaque vise à contourner l'authentification multifacteur.

La technique AiTM consiste  à placer l'attaquant au milieu du processus d'authentification au travers d'un serveur *proxy* afin de voler les identifiants de l'utilisateur durant le processus d'authentification. Microsoft explique d'ailleurs le fonctionnement de cette attaque en détails [sur son blog dédéié à la sécurité.](https://www.microsoft.com/security/blog/2022/07/12/from-cookie-theft-to-bec-attackers-use-aitm-phishing-sites-as-entry-point-to-further-financial-fraud/) Le schéma suivant résume le processus d'attaque :

![ATTAQUE AITM](/assets/img/posts/2022/08/AITM.png)

# Comment se prémunir de ce type d'attaque ? 

- **Utiliser des politiques d'accès conditionnel :** Les politiques d'accès conditionnel sont  appliquées chaque fois qu'un attaquant tente d'utiliser un cookie de session volé. Vous pouvez protéger votre plateforme Microsoft 365 contre les attaques qui exploitent les informations d'identification volées en activant des politiques telles que l'obligation d'utiliser des appareils conformes aux politiques de sécurité définies sur votre plateforme ou en exigeant une connexion depuis une plage d'adresses IP de confiance pour certains de vos utilisateurs.

- **Mettre en place des solutions anti-hameçonnage avancées** qui surveillent et analysent les courriels entrants et les sites Web visités. Implémentez également les protocoles SPF, DKIM et DMARC pour vous prémunir des tentatives d'usurpation d'identité sur vos domaines.  

- Si vous bénéficiez du plan de licence adéquat, sachez que **Microsoft 365 Defender** est en capacité de bloquer les attaque *AiTM* 
![AiTM Defender 365](/assets/img/posts/2022/08/Figure12-stolen-session-cookie.png)

# Bonus : indicateurs de compromission

Microsoft publie les indicateurs de compromission suivants (IOCs) :

## Domaines redirecteurs :

```
32sssaawervvvv[.]biz
adminmmi[.]biz
auth2022[.]live
cleanifl[.]com
docpmsi[.]us
vrtlsrvmapp[.]biz
vrtofcvm[.]live
```

## Domaines des sites de phishing :

```
login[.]actionspsort[.]cam
login[.]akasmisoft[.]xyz
login[.]aueuth11[.]live
login[.]auth009[.]xyz
login[.]auth2022[.]live
login[.]auth83kl[.]live
login[.]bittermann-hh[.]co
login[.]cbhbanlc[.]com
login[.]cleanifl[.]com
login[.]clfonl365[.]xyz
login[.]gddss36[.]live
login[.]grodno-pl[.]com
login[.]hfs923[.]shop
login[.]karlandpearson[.]com
login[.]klm2136[.]click
login[.]login-micro[.]mcrsfts-passwdupdate[.]com
login[.]mcrosfts-updata[.]live
login[.]mcrosfts-update[.]cloud
login[.]mcrosfts-update[.]digital
login[.]mcrosftts-update[.]cloud
login[.]mcrsft-audio[.]xyz
login[.]mcrsfts-cloud[.]live
login[.]mcrsfts-passwd[.]cloud
login[.]mcrsfts-passwd[.]digital
login[.]mcrsfts-passwdupdate[.]com
login[.]mcrsfts-update[.]cloud
login[.]mcrsfts-update[.]digital
login[.]mcrsfts-virtualofficevm[.]com
login[.]mcrsftsvm-app[.]digital
login[.]mcrsftsvm-app[.]live
login[.]mcrsfts-voiceapp[.]digital
login[.]mcrsftsvoice-mail[.]cloud
login[.]microsecurity[.]us
login[.]microstoff[.]xyz
login[.]mljs365[.]xyz
login[.]mwhhncndn[.]xyz
login[.]mycrsfts-passwd[.]live
login[.]qwwxthn[.]xyz
login[.]seafoodsconnection[.]com
login[.]sunmarks[.]co[.]uk
login[.]tfosorcimonline[.]xyz
login[.]whitmanlab[.]uk
login[.]yi087011[.]xyz
```
