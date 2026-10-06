# Guide d'écriture : Markdown et LaTeX pour les Rapports

Ce guide permet de rédiger des comptes-rendus directement dans les fichiers Markdown (`.md`) de notre dépôt.

---

## 1. Les bases de la syntaxe Markdown

Le Markdown permet de mettre en forme du texte simplement, sans s'occuper de la mise en page finale.

### Titres
Utilisez des dièses (`#`) pour créer des titres de différentes tailles :
```markdown
# Titre principal (Niveau 1)
## Titre de section (Niveau 2)
### Sous-titre (Niveau 3)

```

### Texte en gras et en italique

```markdown
Ceci est du texte en **gras** et ceci est en *italique*.

```

### Listes à puces

Pour faire des listes, utilisez des astérisques ou des tirets :

```markdown
* Premier point
* Deuxième point
  * Sous-point

```

### Insérer des blocs de code

Pour illustrer avec du code Python ou afficher des résultats de terminal :

```markdown
```python
# Exemple de code Python
import numpy as np
f = np.linspace(1e9, 3e9, 201) # Fréquence de 1 GHz à 3 GHz
```

```

---

## 2. Intégrer des mathématiques avec LaTeX

Pour toutes vos formules (calculs de dynamique, permittivité, paramètres $S$), vous pouvez utiliser la syntaxe LaTeX directement dans le texte.

### Formules en ligne (dans la phrase)

Pour insérer une formule au milieu d'une phrase, placez-la entre **un seul symbole dollar (`$`)** de chaque côté.

* *Exemple :* `La tension de port est notée $V_1$ et l'impédance caractéristique est $Z_0 = 50\,\Omega$.`
* *Rendu :* La tension de port est notée $V_1$ et l'impédance caractéristique est $Z_0 = 50\,\Omega$.

### Formules en bloc (centrées)

Pour une équation importante, utilisez **deux symboles dollars (`$$`)** de chaque côté :

```markdown
$$
S_{11} = 20 \log_{10}\left(\frac{V_{réfléchi}}{V_{incident}}\right)
$$

```

* *Rendu :*
$$ S_{11} = 20 \log_{10}\left(\frac{V_{réfléchi}}{V_{incident}}\right) $$

### Symboles courants utiles en physique / RF :

* Fractions : `$\frac{numérateur}{dénominateur}$` $\rightarrow$ $\frac{a}{b}$
* Exposants et indices : `$S_{11}$`, `$f^2$` $\rightarrow$ $S_{11}$, $f^2$
* Lettres grecques : `$\alpha$`, `$\beta$`, `$\epsilon_r$` (permittivité relative) $\rightarrow$ $\alpha$, $\beta$, $\epsilon_r$
* Racines carrées : `$\sqrt{x}$` $\rightarrow$ $\sqrt{x}$

---

## 3. Visualiser le résultat en direct (VS Code)

Pour voir à quoi ressemble votre rapport avec la mise en forme et les équations LaTeX joliment affichées :

1. Ouvrez votre fichier `.md` dans **VS Code**.
2. Installez l'extension **Markdown Preview Enhanced**.
3. Faites un clic droit dans l'éditeur de texte et choisissez **"Markdown Preview Enhanced: Open Preview to the Side"** (ou utilisez le raccourci `Ctrl+K` puis `V`).

