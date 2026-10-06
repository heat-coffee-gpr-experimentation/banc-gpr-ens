# Guide d'Installation des Logiciels (Windows & Linux)

Ce guide détaille l'installation de l'environnement de travail indispensable pour le projet GPR (VS Code, Git, Python et les extensions Markdown/LaTeX) pour les postes sous **Windows** et **Linux (Ubuntu/Debian)**.

---

## 1. Installation de Git

Git permet de suivre l'historique du code et de synchroniser votre travail avec GitHub.

### Sous Windows :
1. Téléchargez l'installateur officiel sur [git-scm.com/download/win](https://git-scm.com/download/win).
2. Lancez l'exécutable et suivez les étapes de l'assistant. 
   * *Conseil :* Laissez les options par défaut recommandées par l'installateur (notamment l'utilisation de *Git Bash* et le choix de l'éditeur par défaut).
3. Vérifiez l'installation en ouvrant **Git Bash** ou votre invite de commande et en tapant :
   ```bash
   git --version

```

### Sous Linux (Ubuntu / Debian) :

Ouvrez votre terminal et tapez les commandes suivantes :

```bash
sudo apt update
sudo apt install git

```

Vérifiez l'installation :

```bash
git --version

```

---

## 2. Installation de Visual Studio Code (VS Code)

VS Code est l'éditeur de texte recommandé pour rédiger les rapports en Markdown et écrire les scripts Python.

### Sous Windows :

1. Téléchargez VS Code sur [code.visualstudio.com](https://code.visualstudio.com/).
2. Lancez l'installateur et veillez à cocher l'option **"Ajouter au PATH"** (Add to PATH) pour pouvoir lancer VS Code facilement depuis un terminal.

### Sous Linux (Ubuntu / Debian) :

Téléchargez le paquet `.deb` depuis le site officiel ou installez-le via le terminal :

```bash
sudo apt update
sudo apt install software-properties-common apt-transport-https wget
wget -q [https://packages.microsoft.com/keys/microsoft.asc](https://packages.microsoft.com/keys/microsoft.asc) -O- | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] [https://packages.microsoft.com/repos/vscode](https://packages.microsoft.com/repos/vscode) stable main"
sudo apt update
sudo apt install code

```

Vérifiez l'installation en tapant `code` dans votre terminal.

---

## 3. Installation des extensions indispensables dans VS Code

Pour profiter pleinement du confort de rédaction (Markdown, rendu LaTeX en direct, coloration syntaxique Python), ouvrez VS Code, cliquez sur l'icône des **Extensions** sur le côté gauche (ou `Ctrl+Shift+X` / `Cmd+Shift+X`), puis recherchez et installez les extensions suivantes :

1. **Python** (par Microsoft) : Indispensable pour l'exécution et le lissage du code Python.
2. **Markdown All in One** (par Yu Zhang) : Raccourcis, table des matières automatique et aperçu pour le Markdown.
3. **Markdown Preview Enhanced** (par Shd101wyy) : Indispensable pour visualiser en temps réel vos rapports avec le rendu des équations mathématiques LaTeX.

---

## 4. Installation de Python

Python est nécessaire pour piloter les instruments (comme le VNA via `pyvisa`) et traiter les signaux GPR.

### Sous Windows :

1. Téléchargez Python sur [python.org](https://www.python.org/).
2. **Attention :** Cochez impérativement la case **"Add Python to PATH"** tout en bas de la première fenêtre d'installation.
3. Cliquez sur *Install Now*.

### Sous Linux (Ubuntu / Debian) :

Python est généralement préinstallé sous Linux. Vous pouvez vérifier sa présence et installer l'environnement virtuel avec :

```bash
sudo apt update
sudo apt install python3 python3-pip python3-venv

```

---

## 5. Configuration initiale de Git (À faire une seule fois par poste)

Une fois Git installé, indiquez votre nom et votre adresse e-mail (utilisée sur GitHub) pour signer vos contributions :

```bash
git config --global user.name "Votre Prénom Nom"
git config --global user.email "votre.email@exemple.com"

```

