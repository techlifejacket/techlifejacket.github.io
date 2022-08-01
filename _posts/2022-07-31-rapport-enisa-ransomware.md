---
title: "Rapport 2022 de l'ENISA sur la menace ransomware"
date: 2022-07-31 17:27:00:00 +02:00
author: seb
layout: post
tags: [enisa,ransomware]
categories: sécurité
readtime: true
comments: true
cover-img: "assets/img/banners/ransomware-banner.png"
thumbnail-img: assets/img/posts/2022/07/31/enisa-logo-png.png
---

Je vous livre dans cet article un bref résumé du rapport de l'[ENISA](https://www.enisa.europa.eu/) traitant des menaces de type ransowmware. Le rapport complet est [téléchargeable ici](https://www.enisa.europa.eu/publications/enisa-threat-landscape-for-ransomware-attacks/@@download/fullReport).

# Les rançongiciels : ennemi public n°1
Au cours des dernières années, le paysage des menaces ENISA a régulièrement placé les ransomwares comme la menace numéro un. Grâce à l'émergence d'un modèle commercial de cybercriminalité en tant que service, la répartition du travail est devenue plus spécialisée et organisée, transformant les ransomwares en marchandises. En analysant attentivement 623 événements de ransomware de mai 2021 à juin 2022, ce document offre de nouvelles perspectives sur le scénario de menace de ransomware. L'article commence par définir le rançongiciel précisément parce qu'il est apparu comme une notion illusoire aux multiples dimensions et étapes.

## Quelques rappels

### Définition

Le rançongiciel est un type d'attaque où les acteurs de la menace prennent le contrôle des actifs d'une cible et exigent une rançon en échange du retour de la disponibilité et de la confidentialité des actifs. Il y a trois éléments clés dans chaque attaque de ransomware : les actifs, les actions et le chantage. Les atouts et les actions seront abordés dans la section suivante. Le chantage est le dernier élément clé des attaques de rançongiciels, où des menaces sont faites à la cible par l'utilisation de menaces exigeant quelque chose en échange de la disponibilité des actifs.

### Types de rançongiciels

Les ransomwares peuvent verrouiller l'accès à un actif, comme le verrouillage de l'écran, ou verrouiller l'accès à une application particulière. Il peut chiffrer un actif le rendant indisponible pour la cible. Nous proposons de parler des rançongiciels en termes d'actions qu'ils effectuent et d'actifs qu'ils ciblent. Ces quatre actions principales sont les LEDS (Lock, Encrypt, Delete, Steal). Un ransomware peut voler un actif, compromettre sa disponibilité et au final sa confidentialité.

Les actifs les plus couramment ciblés par les ransomwares sont les fichiers et les dossiers, mais ce ne sont pas les seuls. D'autres actifs ciblés peuvent inclure des bases de données, des systèmes de gestion de contenu, des écrans, des enregistrements de démarrage principaux (MBR), des tables de fichiers maîtres (MFT) et autres. Il est clair que de nombreuses combinaisons sont possibles.

![ENISA](/assets/img/posts/2022/07/31/enisa-ransomware-capabilities.png)

### Cycle de vie d'un rançongiciel

Le cycle de vie des ransomwares est resté inchangé jusqu'en 2018 environ, lorsque les ransomwares ont commencé à ajouter plus de fonctionnalités et que les techniques de chantage ont mûri. 
Il y a cinq étapes dans une attaque par rançongiciel : accès initial, exécution, action sur les objectifs, chantage et négociation de la rançon. Ces étapes ne suivent pas un cheminement strictement séquentiel. 

**Ne négociez jamais avec les cybercriminels, ne payez pas de rançon, vous ne faîtes qu'alimenter leur businness. Bien souvent, ils ne sont pas capables de vous fournir d'outil pour déchiffrer complètement vos données.**

Contacter l'autorité compétente en matière de cybersécurité et/ou les forces de l'ordre est l'approche recommandée pour gérer de tels incidents (en France, contactez l'ANSSI). 

![LIFECYCLE](/assets/img/posts/2022/07/31/enisa-ransomware-lifecycle.png)

# Résumé du rapport ENISA 2022

Ce rapport sur le paysage des menaces a analysé un total de 623 incidents de ransomwares dans l'UE, au Royaume-Uni et aux États-Unis sur une période allant de mai 2021 à juin 2022. Les données ont été recueillies à partir de rapports des gouvernements, d'entreprises du milieu cyber, de la presse, de blogs et, dans certains cas, en utilisant des sources connexes du dark web.

Entre mai 2021 et juin 2022, environ 10 téraoctets de données ont été volés chaque mois par des pirates informatiques. 58,2 % des données volées incluaient les données personnelles des employés.

Au moins 47 acteurs uniques de menace de ransomware ont été trouvés.

Pour 94,2 % des incidents, on ne sait pas si l'entreprise a payé la rançon ou non. Cependant, lorsque la négociation échoue, les attaquants exposent et rendent généralement les données disponibles sur leurs pages Web. C'est ce qui se passe en général et c'est une réalité pour 37,88% des incidents.

On peut donc conclure que les 62,12% d'entreprises restantes sont soit parvenues à un accord avec les attaquants, soit ont trouvé une autre solution.

L'étude montre également que des entreprises de toutes tailles et de tous secteurs sont concernées.


# Bonus : Le cas KASEYA

*Travaillant pour un MSP à l'heure où j'écris ces lignes, ce sujet m'intéresse tout particulièrement.*

Kaseya est une plate-forme de surveillance et de gestion à distance (RMM). Leurs produits sont installés sur les postes de travail clients, les serveurs de gestion des terminaux gérés par des fournisseurs de services gérés (MSP). Un incident en juillet 2021 a entraîné la compromission et le chiffrement de plus de 50 MSP et entre 800 et 1 500 entreprises. Les cyberciminels à l'origine de l'attaque ont exigé de Kaseya et indirectement de ses clients, la somme de 70 millions de dollars en échange d'un outil de déchiffrement de fichiers qui permettrait la restauration des actifs concernés.

_Schéma de l'attaque de la chaîne d'approvisionnement de Kaseya. Les attaquants ont déployé du code sur les instances VSA de fournisseurs MSP (que ce soit dans le cloud ou sur site est toujours à l'étude).
Certains MSP ont été exploités, à leur tour, pour déployer des logiciels malveillants et des rançongiciels chez leurs clients._
![KASEYA](/assets/img/posts/2022/07/31/kaseya-schema.png)
