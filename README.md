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
- Une fois la pull request vérifiée, l'initiateur se charge de la valider, ce qui déclenchera automatiquement la fusion de la branche ```feature/setup``` vers la branche ```main```.
- Tous les membres de l'équipe peuvent ensuite tirer les modifications effectuées, puis se rendre sur main afin de lancer index.html et de voir le résultat du setup dans leur navigateur.

## 🧭 Étape 3 : Interface utilisateur et fonctionnement interne

- C'est bien beau de créer une seule branche pour que tout le monde travaille dessus, mais en pratique ça peut souvent provoquer des conflits, en particulier lorsque l'on travaille à plusieurs sur les mêmes fichiers !
- Pour éviter ce genre de problème, on créé généralement une branche par fonctionnalité de notre programme, sur laquelle une seule personne va travailler à la fois.
- Cette méthodologie permet de minimiser les conflits pendant l'implémentation de nouvelles fonctionnalités, et de regrouper leurs résolutions au moment de la pull request. Nous allons donc l'utiliser pour implémenter l'UI (User Interface) de notre visualisateur du jeu de la vie.
- Afin d'éviter de directement fusionner nos fonctionnalités fraîchement implémentées (et non testées), à notre branche principale (main), on crée une branche intermédiaire appelée ```dev``` qui servira d'espace de test, pour s'assurer du bon fonctionnement de nos fonctionnalités avant de les incorporer à notre produit final.

### 1. Création des branches
- L'initiateur créé une nouvelle branche dev
- L'assureur tire les changements, se rend sur la branche dev, et créé une nouvelle branche feature/ui_html (qui partira donc de ```dev```, et non de ```main```)
- Le réparateur tire les changements, se rend sur la branche dev, et créé une nouvelle branche feature/ui_css (qui partira donc de ```dev```, et non de ```main```)

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

### 4. Pull Requests

- L'initiateur créé deux pull requests, une pour la branche ```feature/ui_html``` vers ```dev```, et une pour la branche ```feature/ui_css``` vers ```dev```
- Tous les membres de l'équipe vérifient ces deux pull requests, puis l'initiateur s'occupe de les valider. 
- Une fois la pull request validée, tous les membres de l'équipe tirent les modifications, puis se rendent sur ```dev``` pour lancer index.html et constater l'évolution du produit grâce à l'implémentation des nouvelles fonctionnalités.
- Une fois ce "test" effectué, l'initiateur créé une nouvelle pull request de ```dev``` vers ```main``` afin d'incorporer la fonctionnalité testée au produit final.
- Rebelotte, tous les membres de l'équipe vérifient la pull request, puis l'initiateur s'occupe de la valider.




⚙️ Étape 4 : Logique du Jeu de la Vie

Nous allons maintenant implémenter la logique algorithmique du jeu de la vie, afin de l'incorporer au projet pour faire fonctionner notre visualisateur.

![Gospers_glider_gun](https://github.com/user-attachments/assets/27146120-8df4-4b2a-a31a-f40319325b51)

## 1. Création de la branche
- L'initiateur créé à partir de la branche ```dev``` une branche ```feature/logic``` qui permettra d'implémenter la logique du jeu de la vie.
- Tous les membres de l'équipe tirent les dernières modifications.


## 2. Implémentation de la logique du jeu de la vie en tant que fonctionnalité
- Le réparateur se rend sur la branche ```feature/logic```, et remplace le contenu de scripts.js par le code suivant :

```
document.addEventListener("DOMContentLoaded", () => {
  const canvas = document.getElementById("gameCanvas");
  if (!canvas) {
    console.error("Canvas introuvable : vérifie l'id 'gameCanvas' dans index.html");
    return;
  }
  const ctx = canvas.getContext("2d");
  if (!ctx) {
    console.error("Impossible d'obtenir le context 2D du canvas.");
    return;
  }

  const cellSize = 10;

  // --- Contrôles UI ---
  const heightInput = document.getElementById("height");
  const widthInput = document.getElementById("width");
  const speedInput = document.getElementById("speed");
  const startBtn = document.getElementById("startBtn");
  const pauseBtn = document.getElementById("pauseBtn");

  // --- Variables du jeu ---
  let rows = parseInt(heightInput?.value || 50, 10);
  let cols = parseInt(widthInput?.value || 50, 10);
  let grid = [];
  let intervalId = null;
  let running = false;
  let cyclesPerSec = parseFloat(speedInput?.value || 5);

  // --- Fonctions principales ---
  function resizeCanvas() {
    canvas.width = cols * cellSize;
    canvas.height = rows * cellSize;
  }

  function createGrid(empty = true) {
    grid = new Array(rows);
    for (let r = 0; r < rows; r++) {
      grid[r] = new Array(cols);
      for (let c = 0; c < cols; c++) {
        grid[r][c] = empty ? 0 : (Math.random() < 0.5 ? 1 : 0);
      }
    }
    resizeCanvas();
  }

  function drawGrid() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    for (let r = 0; r < rows; r++) {
      for (let c = 0; c < cols; c++) {
        ctx.fillStyle = grid[r][c] ? "#fff" : "#000";
        ctx.fillRect(c * cellSize, r * cellSize, cellSize, cellSize);
      }
    }
  }

  function countNeighbors(r, c) {
    let count = 0;
    for (let i = -1; i <= 1; i++) {
      for (let j = -1; j <= 1; j++) {
        if (i === 0 && j === 0) continue;
        const x = r + i, y = c + j;
        if (x >= 0 && x < rows && y >= 0 && y < cols) {
          count += grid[x][y] ? 1 : 0;
        }
      }
    }
    return count;
  }

  function nextGeneration() {
    const newGrid = new Array(rows);
    for (let r = 0; r < rows; r++) {
      newGrid[r] = new Array(cols);
      for (let c = 0; c < cols; c++) {
        const neighbors = countNeighbors(r, c);
        if (grid[r][c]) {
          newGrid[r][c] = (neighbors === 2 || neighbors === 3) ? 1 : 0;
        } else {
          newGrid[r][c] = (neighbors === 3) ? 1 : 0;
        }
      }
    }
    grid = newGrid;
    drawGrid();
  }

  function startSimulation() {
    if (running) return;
    running = true;
    intervalId = setInterval(nextGeneration, 1000 / cyclesPerSec);
  }

  function pauseSimulation() {
    running = false;
    if (intervalId) {
      clearInterval(intervalId);
      intervalId = null;
    }
  }

  function wipeGrid() {
    createGrid(true);
    drawGrid();
  }

  function randomFill() {
    createGrid(false);
    drawGrid();
  }

  // --- Événements UI ---
  startBtn?.addEventListener("click", () => {
    const newRows = parseInt(heightInput.value || 20, 10);
    const newCols = parseInt(widthInput.value || 20, 10);
    const newSpeed = parseFloat(speedInput.value || 5) || 1;

    cyclesPerSec = newSpeed;

    if (newRows !== rows || newCols !== cols) {
      rows = newRows;
      cols = newCols;
      createGrid(true);
      drawGrid();
    }

    startSimulation();
  });

  pauseBtn?.addEventListener("click", () => {
    pauseSimulation();
  });

  document.addEventListener("keydown", (ev) => {
    if (ev.key === "w") wipeGrid();
    else if (ev.key === "r") randomFill();
  });

  canvas.addEventListener("click", (e) => {
    const rect = canvas.getBoundingClientRect();
    const x = e.clientX - rect.left;
    const y = e.clientY - rect.top;
    const c = Math.floor(x / cellSize);
    const r = Math.floor(y / cellSize);
    if (r >= 0 && r < rows && c >= 0 && c < cols) {
      grid[r][c] = grid[r][c] ? 0 : 1;
      drawGrid();
    }
  });

  // --- Initialisation par défaut ---
  createGrid(true); // grille aléatoire
  drawGrid();

  // Simulation automatique
  running = true;
  intervalId = setInterval(nextGeneration, 1000 / cyclesPerSec);

  // --- Console debug ---
  window.gameDebug = { wipeGrid, randomFill, nextGeneration, startSimulation, pauseSimulation, createGrid };
  console.log("Jeu de la Vie initialisé : simulation automatique en cours !");
});

```

- Puis, il ajoute le fichier script.js à l'index
- Créé un nouveau commit pour enregistrer les changements
- Tire les derniers changements pour s'assurer d'être à jour
- Et finalement, pousse son commit sur le répo distant


## 3. Pull request

- L'initiateur créé une pull request pour ```feature/logic``` vers ```dev``` afin d'intégrer la nouvelle fonctionnalité.
- Les membres de l'équipe la review et la vérifie, puis l'initiateur la valide.
- Tout le monde tire les changements et se rend sur ```dev``` pour lancer index.html histoire tester la nouvelle fonctionnalité...

![200w](https://github.com/user-attachments/assets/f8d12336-4cee-4c1c-83fc-8158add8a771)

## Ca ne marche pas...

Sacrebleu. Le réparateur était pourtant sûr d'avoir correctement implémenté la logique du jeu de la vie ! Alors, pourquoi rien ne se passe à l'écran lorsque la page s'ouvre ?


