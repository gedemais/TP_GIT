# TP Git – Collaboration en trinôme : Jeu de la Vie (HTML/CSS/JS)

## 🎯 Objectifs du TP
Ce TP a pour but de vous apprendre à utiliser **Git** et **GitHub** dans un cadre de travail collaboratif.  
Vous travaillerez **en trinôme** avec trois rôles bien définis :

- 🧱 **L’initiateur** : crée le dépôt, initialise le projet et les premières branches.
- 🧩 **L’assureur** : relit les pull requests, valide les merges, s’assure de la propreté du dépôt.
- 🛠️ **Le réparateur** : corrige les bugs, résout les conflits, gère les branches *hotfix*.

Vous ne devez **écrire aucune ligne de HTML, CSS ou JS**.  
Votre travail consiste uniquement à **gérer Git** : création de branches, commits, merges, pull requests, résolution de conflits, etc.

---

## 🧑‍💻 Outils
- Système : **Windows**
- Environnement : **VSCode**
- Utilisation **exclusive du terminal Git intégré à VSCode**
- Aucune interface graphique Git

---

## 📦 Étape 0 : Mise en place de l’équipe et du dépôt

0. Les membres de l'équipe choisissent leurs rôles de départ.
1. Chaque membre crée son compte GitHub.  
2. L’**initiateur** crée un **nouveau dépôt public GitHub** nommé :  jeu-de-la-vie
3. L’initiateur ajoute les deux autres membres comme **collaborateurs**.
4. Chaque membre **clone le dépôt** dans VSCode :
```bash
git clone https://github.com/<pseudo_github_de_l_initiateur>/jeu-de-la-vie.git
```
5. Les trois membres de l'équipe vérifient qu'ils peuvent pousser des modifications en créant un fichier README_<pseudo_github>.md, et en le poussant sur le répo distant après l'avoir commit.
6. Les trois membres de l'équipe vérifient qu'ils peuvent tirer les modifications faites par les deux autres membres de leur groupe.

## ⚙️ Étape 1 : Initialisation du projet
