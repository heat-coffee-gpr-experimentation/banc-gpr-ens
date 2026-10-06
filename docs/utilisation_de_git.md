#  Guide Pratique : Utiliser GitHub pour le Projet GPR

Ce guide vous accompagne pas à pas pour récupérer le projet, travailler sur le code ou les rapports, et partager les modifications sur GitHub.

---

## 1. Les prérequis sur votre ordinateur

Pour commencer, vous avez besoin de deux outils principaux :
1. **Git** : Le logiciel de gestion de version.
2. **VS Code** (recommandé) : Un éditeur de texte gratuit et puissant qui gère très bien le Markdown, le LaTeX et le code Python.

---

## 2. La première installation (À faire une seule fois)

Ouvrez votre terminal (ou l'invite de commande) et tapez les commandes suivantes pour télécharger le projet sur votre ordinateur :

1. **Cloner (copier) le dépôt sur votre machine :**
   ```bash
   git clone [https://github.com/heat-coffee-gpr-experimentation/banc-gpr-ens.git](https://github.com/heat-coffee-gpr-experimentation/banc-gpr-ens.git)
   cd banc-gpr-ens

```

## 3. Le cycle de travail quotidien (Le "Rituel" Git)

Chaque fois que vous commencez une journée de travail ou une nouvelle tâche, suivez ce cycle en 4 étapes simples.

### Étape 1 : Récupérer le travail à jour

Avant de toucher au moindre fichier, assurez-vous de récupérer la dernière version (au cas où un collègue aurait fait des modifications) :

```bash
git pull

```

### Étape 2 : Travailler et créer/modifier vos fichiers

Faites vos modifications :

* Écrivez ou complétez vos comptes-rendus dans le dossier `reports/` (ex: `reports/semaine_02.md`).
* Écrivez vos scripts Python dans le dossier `code/` (ex: `code/acquisition/test_vna.py`).

### Étape 3 : Enregistrer vos modifications localement (Commit)

Une fois que votre travail avance ou qu'une tâche est finie, vous devez dire à Git d'enregistrer une photo ("commit") de vos changements :

1. **Sélectionner les fichiers modifiés :**
```bash
git add .

```


2. **Valider les modifications avec un message explicite :**
```bash
git commit -m "Ajout du compte-rendu de la semaine 2 et script de test VNA"

```



### Étape 4 : Envoyer sur GitHub (Push)

Pour que l'équipe (le responsable, la doctorante) puisse voir votre travail, envoyez vos modifications sur le serveur GitHub :

```bash
git push

```

---

## 4. Résumé des commandes essentielles à garder sous les yeux

| Action | Commande Git | À quoi ça sert ? |
| --- | --- | --- |
| **Mettre à jour** | `git pull` | Récupère le travail des autres sur votre PC. |
| **Vérifier l'état** | `git status` | Affiche la liste des fichiers modifiés. |
| **Préparer** | `git add .` | Sélectionne tous vos nouveaux fichiers/modifications. |
| **Enregistrer** | `git commit -m "Message"` | Enregistre l'historique sur votre PC avec une description. |
| **Publier** | `git push` | Envoie vos enregistrements sur GitHub. |

---

## 5. Bonnes pratiques pour l'équipe

* **Des commits réguliers :** Ne faites pas un seul gros commit à la fin de la semaine. Faites de petits commits clairs au fil de l'eau (ex: "Correction bug lecture VNA", "Fin rédaction partie 1 rapport").
* **Pas de données lourdes :** Ne commitez **jamais** les gros fichiers de mesures brutes du VNA (fichiers `.s1p`, `.s2p` volumineux) sur GitHub. Utilisez l'espace partagé du labo (Nextcloud / NAS) pour cela. GitHub est réservé au code et aux rapports textuels.
* **Écriture des rapports :** Rédigez vos bilans dans `reports/` au format Markdown (`.md`) en utilisant les balises LaTeX pour vos formules (ex: `$S_{11}$`). Vous pouvez utiliser l'extension *Markdown Preview Enhanced* dans VS Code pour voir le résultat mis en forme en direct.

