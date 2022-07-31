---
title: "Création du blog, premier tuto avec Jekyll"
date: 2022-07-27 23:27:00:00 +02:00
author: seb
layout: post
image: /assets/img/2021/06/deep-fried.png
tags: jekyll
categories: tuto
readtime: true
comments: true
cover-img: "https://jekyllrb.com/img/jekyll-og.png"
thumbnail-img: /assets/img/hello_world.jpeg
---

# Pourquoi Jekyll ?
Je considère que bloguer devrait seulement être un travail d'écriture et pas un travail d'admin système sans fin où le quotidien est fait d'installation de mises à jour de sécurité, de gestion de plugins et d'ajustement des performances d’un site Web afin que les pages se chargent rapidement... Clairement, j'ai d'autres chats à fouetter. 

Après quelques recherches, je me suis tourné vers Jekyll, qui est une solution s'appuyant sur Ruby. Pas d'interface d'administration, seulement des fichiers sources créés à partir d'un terminal (ça, c'est mon côté geek qui ressort). Jekyll est capable de convertir vos fichiers HTML ou Markdown en contenu statique, en s'appuyant sur un thème pour la mise en page.

Ce tutoriel vous guidera à travers les sujets suivants :

- Comment créer un blog Jekyll sous Windows
- Configuration de votre blog Jekyll
- Rédaction d’articles et de pages en Markdown
- Hébergement de votre blog à l’aide de GitHub Pages

# Conditions préalables
Pour suivre ce didacticiel, vous devez utiliser une version récente du système d’exploitation Windows. Vous aurez également besoin de Visual Studio Code (ou d’un éditeur de code similaire), de Git pour Windows (ou de votre client Git préféré) et d’un compte GitHub si vous souhaitez utiliser GitHub Pages.

# Comment installer Jekyll sur Windows
Jekyll est écrit en Ruby comme un joyau, donc pour exécuter Jekyll sur Windows, nous devrons d’abord télécharger et installer RubyInstaller pour Windows. Assurez-vous de télécharger une version récente de Ruby+DevKit et d’utiliser les options par défaut de l’assistant d’installation. À la dernière étape, vous voudrez garder l’option « Exécuter 'ridk install' pour configurer MSYS2 et la chaîne d’outils de développement. » cochée.

Vous avez presque installé Ruby sur Windows! Une fois l’assistant d’installation terminé, vous devriez voir une invite de commande pour configurer MSYS2 et la chaîne d’outils de développement. Entrez simplement 1 dans l’invite de commande pour installer l’installation de base MSYS2.

Vous pouvez maintenant fermer l’invite de commande et en ouvrir une nouvelle, car maintenant que nous avons installé Ruby, il est temps d’installer Jekyll! Dans la nouvelle invite de commandes, exécutez la commande :

```bash
gem install jekyll bundler
```

Confirmons que Jekyll est installé sur Windows en sortant la version de Jekyll sur notre machine. Pour ce faire, exécutez la commande :

```bash
jekyll -v
```

Vous êtes maintenant prêt à utiliser Jekyll dans la ligne de commande pour créer votre nouveau blog!

Comment créer un nouveau blog à l’aide de Jekyll
En utilisant Jekyll, nous pouvons utiliser une commande pour créer un nouveau blog avec un thème, un article et une page par défaut. Créez un nouveau dossier sur votre PC pour votre blog Jekyll et utilisez son chemin complet comme paramètre dans la commande suivante :

```bash
jekyll new PATH
```

C’est tout ! Si vous vérifiez le dossier, Jekyll aura créé les fichiers nécessaires pour votre nouveau blog; y compris le thème Minima par défaut, un exemple de publication et de page et les paramètres de configuration par défaut.

Voyons à quoi ça ressemble! Je vais utiliser l’éditeur de code gratuit Visual Studio Code de Microsoft pour le reste de ce didacticiel pour exécuter des commandes dans un terminal et pouvoir modifier les fichiers Jekyll dans le même espace de travail.

Ouvrez le dossier Jekyll dans Visual Studio Code et créez un nouveau terminal (Ctrl+'). Maintenant, nous pouvons exécuter la commande pour construire et servir localement notre blog Jekyll:

```bash
jekyll serve
```

Une fois que Jekyll a utilisé les fichiers sources pour créer le site Web, nous pouvons maintenant utiliser l’adresse du serveur générée par Jekyll pour afficher notre nouveau blog localement dans le navigateur.

Félicitations! Vous avez maintenant un blog Jekyll utilisant les paramètres par défaut exécutés localement sur votre PC.


# Pour l'hébergement : GitHub Pages !
Parce que Jekyll a été construit par Tom Preston-Werner, le co-fondateur de GitHub, Jekyll fonctionne exceptionnellement bien avec les pages GitHub.

GitHub Pages est un service d'hébergement de site Web statique qui vous permet d'héberger un site Web (statique) directement à partir d'un référentiel GitHub public. 

L'un des grands avantages de l'utilisation de Jekyll avec GitHub Pages est que vous pouvez écrire un nouveau billet de blog, le valider dans le dépôt GitHub qui est utilisé pour héberger votre blog et votre site Web sera automatiquement créé pour publier le nouvel article. C'est pourquoi Jekyll et les pages GitHub fonctionnent très bien ensemble !

Créons un nouveau référentiel GitHub afin de pouvoir publier notre nouveau blog Jekyll sur les pages GitHub. Dans votre compte GitHub, créez le référentiel username.github.io, en vous assurant que username est le nom d'utilisateur de votre compte GitHub.


Clonez le nouveau référentiel sur votre PC à l’aide de git :

```bash
git clone https://github.com/username/username.github.io
```

Copiez et collez tous vos fichiers Jekyll dans le nouveau référentiel local de votre PC et transférez vos modifications dans le référentiel :

```bash
git add --all
git commit -m "Initial commit of Jekyll blog"
git push -u origin main
```

Voilà! Vous pourrez maintenant consulter votre blog Jekyll à l’adresse https://username.github.io.

# Conclusion
J’espère que vous avez apprécié d’en apprendre davantage sur Jekyll et sur la façon dont il peut être utilisé comme une plateforme de blogging puissante mais simple.