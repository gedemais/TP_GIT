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

- Les membres de l'équipe choisissent leurs rôles de départ.
- Chaque membre crée son compte GitHub.  
- L’**initiateur** crée un **nouveau dépôt public GitHub** nommé :  jeu-de-la-vie
- L’initiateur ajoute les deux autres membres comme **collaborateurs**.
- Chaque membre **clone le dépôt** dans VSCode :
```bash
git clone https://github.com/<pseudo_github_de_l_initiateur>/jeu-de-la-vie.git
```
- Les trois membres de l'équipe vérifient qu'ils peuvent pousser des modifications en créant un fichier README_<pseudo_github>.md, en écrivant leur prénom à l'intérieur, et en le poussant sur le répo distant après l'avoir commit.
- Une fois l'étape précédente terminée, chaque membre de l'équipe vérifie qu'il peut tirer les modifications faites par les deux autres membres.

📁 Structure du projet (finale)
```
jeu-de-la-vie/
│
├── index.html
├── style.css
├── script.js
├── README_a.md
├── README_b.md
└── README_c.md
```


## ⚙️ Étape 1 : Initialisation du projet


### 1. Installation du fichier HTML

- L’initiateur crée la branche ```feature/setup```
- Il y ajoute le fichier index.html en y copiant le code HTML suivant :
```
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>Jeu de la Vie</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <h1>Jeu de la Vie</h1>
  <canvas id="gameCanvas"></canvas>
  <script src="script.js"></script>
</body>
</html>
```

- Puis, il ajoute le fichier index.html à l'index
- Créé un nouveau commit pour enregistrer les changements
- Tire les derniers changements pour s'assurer d'être à jour
- Et finalement, pousse son commit sur le répo distant

#### Les deux étapes suivantes peuvent être réalisées en même temps.

### 2. Installation du fichier JavaScript

- L'assureur tire (pull) les modifications faites par l'initiateur.
- Il se déplace sur la branche ```feature/setup```
- Il y ajoute le fichier scripts.js en y copiant le code JavaScript suivant :

```
console.log("Jeu de la Vie - Initialisation");
```

- Puis, il ajoute le fichier scripts.js à l'index
- Créé un nouveau commit pour enregistrer les changements
- Tire les derniers changements pour s'assurer d'être à jour
- Et finalement, pousse son commit sur le répo distant


### 3. Installation du fichier CSS

- Le réparateur tire (pull) les modifications faites par l'initiateur.
- Il se déplace sur la branche ```feature/setup```
- Il y ajoute le fichier style.css en y copiant le code CSS suivant :

```
body {
  font-family: Arial, sans-serif;
  text-align: center;
  background: #fafafa;
}

canvas {
  border: 1px solid #333;
}

```
- Puis, il ajoute le fichier style.css à l'index
- Créé un nouveau commit pour enregistrer les changements
- Tire les derniers changements pour s'assurer d'être à jour
- Et finalement, pousse son commit sur le répo distant


### 4. Synchronisation

![power-power-rangers](https://github.com/user-attachments/assets/08d59d64-bd58-4c8b-881d-d652d5957210)

Pour que tous les membres de l'équipe soient à jour sur les dernières modifications apportées au répo distant, ils doivent les récupérer localement en les tirant.

## ⚙️ Étape 2 : Première Pull Request

### 1. Création de la pull request
- L'initiateur doit se rendre sur github et créer une pull request de la branche ```feature/setup``` vers la branche main.
- La pull request ne doit pouvoir être validée que si elle est vérifiée par les trois membres de l'équipe.


### 2. Vérification et validation de la pull request
- Les trois membres de l'équipe passent en revue les modifications apportées par la branche ```feature/setup```, en vérifiant que chaque membre y a bien ajouté le bon fichier avec le bon contenu.
- Une fois les vérifications effectuées, chaque membre de l'équipe doit vérifier la pull request
- Une fois la pull request vérifiée, l'initiateur se charge de la valider.



## 🧭 Étape 3 : Interface utilisateur et fonctionnement interne

- C'est bien beau de créer une seule branche pour que tout le monde travaille dessus, mais en pratique ça peut souvent provoquer des conflits, en particulier lorsque l'on travaille à plusieurs sur les mêmes fichiers !
- Pour éviter ce genre de problème, on créé généralement une branche par fonctionnalité de notre programme, sur laquelle une seule personne va travailler à la fois.
- Cette méthodologie permet de minimiser les conflits pendant l'implémentation de nouvelles fonctionnalités, et de regrouper leurs résolutions au moment de la pull request. Nous allons donc l'utiliser pour implémenter l'UI (User Interface) de notre visualisateur du jeu de la vie.

### 1. Création des branches
- L'initiateur créé une nouvelle branche feature/ui_html
- L'assureur créé une nouvelle branche feature/ui_css

#### Les deux étapes suivantes peuvent être réalisées en même temps.

### 2. Implémentation du panneau de contrôle

- L'initiateur modifie index.html pour ajouter un panneau de contrôle :

```
<div id="controls">
  <label>Hauteur: <input id="height" type="number" value="20"></label>
  <label>Largeur: <input id="width" type="number" value="20"></label>
  <label>Cycles/sec: <input id="speed" type="number" value="5"></label>
  <button id="startBtn">▶️ Démarrer</button>
  <button id="pauseBtn">⏸️ Pause</button>
</div>
```

- Puis, il ajoute le fichier index.html à l'index
- Créé un nouveau commit pour enregistrer les changements
- Tire les derniers changements pour s'assurer d'être à jour
- Et finalement, pousse son commit sur le répo distant


### 3. Amélioration du style du panneau de contrôle

- L'assureur modifie style.css pour styliser le panneau de contrôle :

```
#controls {
  margin: 20px;
}

#controls label {
  margin: 0 10px;
}

```

- Puis, il ajoute le fichier style.css à l'index
- Créé un nouveau commit pour enregistrer les changements
- Tire les derniers changements pour s'assurer d'être à jour
- Et finalement, pousse son commit sur le répo distant


