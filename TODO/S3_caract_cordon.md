# Recette de caractérisation de deux cordons SMA 5 m — Banc GPR 2–18 GHz

*F. D. Dernière modification : 13 octobre 2026*

## Objectifs

* Caractériser les deux cordons coaxiaux SMA de 5 m destinés au radar GPR Heat Coffee, sur la bande utile **2–18 GHz**. 
* Mesurer les pertes d’insertion $S_{21}$ et $S_{12}$, l’adaptation via le $S_{11}$ et $S_{22}$, le ROS, 
* Mesurer la phase de transmission, sa stabilité  sous torsion,
* Mesurer la dérive temporelle .

Les cordons flexibles peuvent présenter une variation des perte d'insertions et de la phase sous mouvement mécanique. 

## Matériel et conditions

### Matériel

- VNA **R&S ZNB3020**, 2 ports, 9 kHz–20 GHz. [rohde-schwarz](https://www.rohde-schwarz.com/us/products/test-and-measurement/vnas/rs-znb3000-vector-network-analyzer_334291.html)
- Deux cordons SMA à caractériser, notés **Câble A** et **Câble B**, longueur 5 m, DC–20 GHz.
- Kit d’étalonnage SMA adapté au connecteur du ZNB, calibré et caractérisé jusqu’à 20 GHz.
- Deux cordons d’étalonnage courts, phase-stables si possible, SMA mâle/femelle selon la configuration.
- Clé dynamométrique SMA calibré, 
- Adaptateurs SMA nécessaires, charge 50 Ω, court-circuit et open du kit.
- Support non métallique pour poser le câble sans contrainte.
- Gabarits de torsion : mandrins ou supports permettant un rayon de courbure constant, par exemple 100 mm, 200 mm et 300 mm.
- Thermomètre de laboratoire.
- PC.

### Conditions environnementales

- Température de salle : à relever.
- Le VNA et les cordons doivent être laissés dans la salle au moins **1 h** avant mesure.
- Éviter les mouvements de câbles pendant l’acquisition : les cordons flexibles peuvent varier de quelques dixièmes de dB sous flexion. [sigmarf](https://www.sigmarf.com/blog/how-to-measure-rf-cable-loss-accurately/)

## Préparation 

1. Inspecter visuellement les connecteurs SMA : pas de bague tournante bloquée, pas de pin plié, pas de saleté ni de rayure sur le diélectrique.
2. Serrer tous les raccords à la clé dynamométrique. 
3. Identifier chaque cordon : `CABLE_A_SNxxx` et `CABLE_B_SNxxx`.


## Configuration du ZNB3020

### Canal de mesure

| Paramètre | Valeur recommandée |
|---|---|
| Bande de fréquence | 2 GHz à 18 GHz |
| Nombre de points | 4 001 ou plus |
| Type de balayage | Linéaire en fréquence |
| Puissance de source | 0 dBm |
| Bande IF | 100 Hz à 1 kHz |
| Moyennage | 10 à 20 moyennes |
| Correction d’erreur | Full 2-port |
| Format S21 | dB + phase |
| Format S11 | dB, Smith, VSWR |
| Sauvegarde | .s2p + captures écran + état VNA |

### Traces à afficher

- Trace 1 : $S_{21}$ en dB.
- Trace 2 : $S_{21}$ en phase, de préférence phase non enroulée.
- Trace 3 : $S_{11}$ en dB.
- Trace 4 : $S_{11}$ en VSWR.
- Trace 5 : $S_{22}$ en dB.
- Trace 6 : $S_{22}$ en VSWR.

## Étalonnage VNA

### Choix de la méthode

* Utiliser une **calibration full 2-port SOLT**. Le plan de référence doit être situé aux extrémités des cordons d’étalonnage courts, c’est-à-dire directement aux points où le cordon de 5 m sera connecté. 

### Procédure

1. Raccorder les deux cordons d’étalonnage courts aux ports 1 et 2 du ZNB3020.
2. Vérifier que ces cordons restent parfaitement immobiles pendant toute la campagne.
3. Lancer l’assistant de calibration : `CHANNEL > CAL > Start Cal`.
4. Sélectionner :
   - Ports : 1 et 2.
   - Connecteur : SMA.
   - Kit : kit réellement utilisé.
   - Type : Full 2-Port.
5. Réaliser chaque standard dans l’ordre indiqué par le VNA.
6. Appliquer la correction.
7. Sauvegarder le calibrage sous un nom explicite :

```text
ZNB3020_SOLT_SMA_2-18GHz_YYYY-MM-DD.cal
```

8. Vérification rapide :
   - Connecter un Thru : $|S_{21}| \approx 0\ \mathrm{dB}$.
   - Connecter une charge : $|S_{11}| < -30\ \mathrm{dB}$ idéalement, ou selon la qualité du kit.
   - Vérifier que la phase du Thru reste proche de 0° sur toute la bande.

> **Attention :** les cordons d’étalonnage ne doivent jamais être tordus ni déplacés après calibration. Sinon, la correction devient invalide.

---

## Mesure "statique" des cordons

> **Attention :** Remplacer, si nécessaire, la configuration « câble droit » par une **couronne lâche à un seul étage**, posée sur un support non métallique, avec un diamètre et un sens d’enroulement fixes. La référence devient alors :

> $$
\text{Configuration } T_0 = \text{couronne lâche reproductible}
> $$

> et non « câble tendu ».

> C’est cohérent avec les pratiques de caractérisation de câbles : les essais de stabilité en phase utilisent un mandrin, une normalisation dans une position initiale, puis une flexion contrôlée d’un tour complet autour du mandrin. Pour les essais de dérive thermique, les normes recommandent également de placer les échantillons en **couronnes lâches**, avec un diamètre au moins égal à 10 fois le rayon minimal statique du câble. [mouser](https://www.mouser.com/datasheet/2/431/GORE_PhaseFlex_092612-274816.pdf)

> L'annexe A1 preésente plus en détail cette configuration

### Montage

```text
ZNB Port 1 ── cordon étalonnage court ── [Câble DUT 5 m] ── cordon étalonnage court ── ZNB Port 2
```

### Procédure pour chaque cordon

1. Sélectionner le calibrage `ZNB3020_SOLT_SMA_2-18GHz`.
2. Connecter le **Câble A** entre les plans de référence.
3. Serrer au couple.
4. Attendre 2 min pour stabilisation mécanique et thermique.
5. Lancer la mesure $S_{11}, S_{21}, S_{22}$, et $S_{12}$.
6. Moyenner si nécessaire.
7. Sauvegarder :

```text
CABLE_A_SNxxx_straight_2-18GHz.s2p
CABLE_A_SNxxx_straight_2-18GHz_state.znb
CABLE_A_SNxxx_straight_2-18GHz.png
```

8. Répéter pour le **Câble B**.
9. Refaire une seconde mesure de chaque cordon pour estimer la répétabilité de connexion.

### Critères d’acceptation indicatifs

Ces seuils sont à ajuster selon la fiche technique du fabricant.

| Grandeur | Critère indicatif sur 2–18 GHz |
|---|---|
| Pertes d’insertion $S_{21}$ et $S_{12}$ | Régulières, sans résonance marquée ; conforme à la fiche constructeur |
| ROS $S_{11}$ | $< 1,5$ sur la majorité de la bande |
| Perte de retour $RL$ | $> 14\ \mathrm{dB}$ si ROS $<1,5$ |
| Répétabilité de connexion | $< 0,05\ \mathrm{dB}$ sur le module de $S_{21}$|
| Phase | Continue, sans saut brutal non expliqué |

---

## Test de stabilité en phase sous torsion

### Objectif

Déterminer si la torsion ou la flexion du cordon modifie significativement la phase de $S_{21}$. C’est essentiel pour un GPR : une variation de phase peut dégrader la cohérence entre les voies d’émission et de réception.

La méthode s’inspire des protocoles industriels consistant à normaliser le câble en position droite, puis à l’enrouler autour d’un mandrin selon un rayon imposé et à mesurer la variation de phase. [blog.minicircuits](https://blog.minicircuits.com/more-than-just-a-phase-understanding-phase-stability-in-rf-test-cables/)

### Définition de l’indicateur

Pour chaque configuration mécanique $k$, on calcule :

$$
\Delta\phi_k(f) = \mathrm{unwrap}\left[\phi_k(f)\right] - \mathrm{unwrap}\left[\phi_0(f)\right]
$$

où $\phi_0(f)$ est la phase en position droite de référence.

On peut aussi exprimer la dérive en retard de groupe équivalent :

$$
\Delta\tau_k(f) =
-\frac{1}{2\pi}
\frac{d\Delta\phi_k(f)}{df}
$$

Enfin, à une fréquence donnée $f_i$, la variation de phase peut être convertie en variation électrique de longueur :

$$
\Delta L_{\mathrm{éq}}(f_i)
=
\frac{c}{2\pi f_i}
\Delta\phi_k(f_i)
$$

Avec $c = 3\times10^8\ \mathrm{m/s}$.

### Configurations à tester

Pour chaque cordon :

| Test | Configuration |
|---|---|
| T0 | Câble droit, référence |
| T1 | Torsion de $+90^\circ$ sur 1 m central |
| T2 | Torsion de $+180^\circ$ sur 1 m central |
| T3 | Torsion de $-90^\circ$ sur 1 m central |
| T4 | Torsion de $-180^\circ$ sur 1 m central |
| T5 | Boucle sur mandrin $R=300\ \mathrm{mm}$ |
| T6 | Boucle sur mandrin $R=200\ \mathrm{mm}$ |
| T7 | Boucle sur mandrin $R=100\ \mathrm{mm}$, si compatible avec le rayon minimal du câble |

> **Sécurité mécanique :** ne jamais dépasser le rayon de courbure minimal indiqué par le fabricant. Un cordon SMA 5 m peut être électriquement spécifié jusqu’à 20 GHz tout en étant mécaniquement fragile près des connecteurs.

### Procédure détaillée

1. Revenir à la configuration droite **T0**.
2. Mesurer et sauvegarder la référence :

```text
CABLE_A_T0_straight.s2p
```

3. Appliquer la configuration **T1** sans débrancher le câble.
4. Attendre 30 s.
5. Mesurer $S_{21}$ sur 2–18 GHz.
6. Sauvegarder :

```text
CABLE_A_T1_torsion_plus90.s2p
```

7. Revenir à T0 et vérifier que la phase revient proche de la référence.
8. Répéter pour T2 à T7.
9. Faire au moins **3 cycles** pour T1, T2, T3 et T4 afin d’évaluer la répétabilité.
10. À la fin, remesurer T0. Si la phase ne revient pas à la référence, le câble présente une hystérésis mécanique.

### Analyse attendue

Tracer pour chaque configuration :

- $\Delta\phi(f)$ de 2 à 18 GHz.
- $\Delta\phi$ à 2, 6, 10, 14 et 18 GHz.
- $|S_{21}|$ avant et après torsion.
- ROS avant et après torsion.

Un résultat acceptable serait par exemple une variation de phase inférieure à quelques degrés sur la bande. À titre de comparaison, certains câbles VNA phase-stables sont spécifiés avec une stabilité en flexion de l’ordre de $\pm 2^\circ$. Un cordon standard de 5 m peut être nettement moins stable ; l’objectif est donc d’établir sa propre limite expérimentale. 

---

## Vérification de réciprocité : $S_{21}$ contre $S_{12}$

Il faut ajouter une **vérification de réciprocité** : pour un cordon passif, linéaire et sans composant non réciproque, $S_{21}$ et $S_{12}$ doivent être identiques en amplitude **et** en phase. Cette comparaison est aussi un excellent contrôle de qualité de l’étalonnage full 2-port et du montage. [dl.cdn-anritsu](https://dl.cdn-anritsu.com/en-us/test-measurement/files/Technical-Notes/White-Paper/11410-00988A.pdf)


### Indicateurs de cohérence

On définit l’écart complexe :

$$
\Delta S_{\mathrm{rec}}(f) = S_{21}(f) - S_{12}(f)
$$

L’écart d’amplitude en dB est :

$$
\Delta IL_{\mathrm{rec}}(f)
=
20\log_{10}\left|S_{21}(f)\right|
-
20\log_{10}\left|S_{12}(f)\right|
$$

L’écart de phase, après dé-enroulement, est :

$$
\Delta\phi_{\mathrm{rec}}(f)
=
\mathrm{unwrap}\left[\arg S_{21}(f)\right]
-
\mathrm{unwrap}\left[\arg S_{12}(f)\right]
$$

On peut aussi calculer une erreur relative complexe :

$$
\epsilon_{\mathrm{rec}}(f)
=
\frac{|S_{21}(f)-S_{12}(f)|}
{\frac{1}{2}\left(|S_{21}(f)|+|S_{12}(f)|\right)}
$$

Cette dernière grandeur est particulièrement utile lorsque le câble présente des pertes importantes.

### Critères d’acceptation proposés

Pour un cordon SMA passif de 5 m, sur 2–18 GHz :

| Grandeur | Critère indicatif | Interprétation |
|---|---:|---|
| $\Delta IL_{\mathrm{rec}}$ | $< 0,05\ \mathrm{dB}$ | Très bonne cohérence |
| $\Delta IL_{\mathrm{rec}}$ | $0,05$ à $0,10\ \mathrm{dB}$ | Acceptable, à surveiller |
| $\Delta IL_{\mathrm{rec}}$ | $> 0,10\ \mathrm{dB}$ | Problème probable : calibration, connecteur ou mesure |
| $\Delta\phi_{\mathrm{rec}}$ | $< 1^\circ$ | Très bonne cohérence |
| $\Delta\phi_{\mathrm{rec}}$ | $1^\circ$ à $3^\circ$ | Acceptable selon la fréquence et le câble |
| $\Delta\phi_{\mathrm{rec}}$ | $> 3^\circ$ | Vérifier calibration, serrage, stabilité mécanique et réciprocité réelle |

Ces seuils sont des critères pratiques de recette, à ajuster selon la fiche technique du câble et la qualité du kit d’étalonnage.

---

## Test de dérive dans le temps

### Objectif

Vérifier que les paramètres du cordon restent stables lorsque la température, la contrainte mécanique et l’état du VNA évoluent lentement.

La documentation R&S indique que la stabilité en température du ZNB est évaluée par des mesures répétées d’une connexion Thru entre 18 et 28 °C, et que la dérive de phase croît linéairement avec la fréquence. 

### Protocole 

1. Laisser le banc sous tension pendant **1 h**.
2. Réaliser la calibration.
3. Connecter le Câble A en position droite.
4. Mesurer immédiatement : $t = 0\ \mathrm{min}$.
5. Puis mesurer à :

```text
t = 0, 5, 15, 30, 60, 120 min
```

6. Enregistrer à chaque instant :
   - $S_{21}$ amplitude et phase.
   - $S_{11}$.
   - Température ambiante.
   - Température du châssis VNA si accessible.
7. Ne toucher ni aux connecteurs ni au câble pendant la durée du test.
8. Répéter pour le Câble B.

Tracer :

- $|S_{21}|(t)$ à 2, 10 et 18 GHz.
- $\phi_{21}(t)$ à 2, 10 et 18 GHz.
- $\Delta\phi(f)$ entre $t=0$ et $t=120\ \mathrm{min}$.
- Corrélation entre $\Delta\phi$ et $\Delta T$.

---

##  Exploitation des fichiers

### Format Touchstone

Chaque mesure doit être exportée en `.s2p`, avec au minimum :

```text
# HZ S RI R 50
```

ou, plus pratique pour l’analyse :

```text
# GHZ S MA R 50
```

Le fichier contient alors, pour chaque fréquence :

$$
f,\ |S_{11}|,\ \angle S_{11},\ |S_{21}|,\ \angle S_{21},\ |S_{12}|,\ \angle S_{12},\ |S_{22}|,\ \angle S_{22}
$$

### Script Python minimal

```python
import numpy as np
import matplotlib.pyplot as plt
from skrf import Network

ref = Network("CABLE_A_T0_straight.s2p")
flex = Network("CABLE_A_T5_loop_R300mm.s2p")

f = ref.f / 1e9

dphi = np.unwrap(np.angle(ref.s[:,1,0])) - np.unwrap(np.angle(flex.s[:,1,0]))
dphi_deg = np.degrees(dphi)

il_ref = 20*np.log10(np.abs(ref.s[:,1,0]))
il_flex = 20*np.log10(np.abs(flex.s[:,1,0]))
d_il = il_flex - il_ref

plt.figure()
plt.plot(f, dphi_deg)
plt.xlabel("Fréquence [GHz]")
plt.ylabel(r"$\Delta\phi_{21}$ [°]")
plt.title("Stabilité en phase sous flexion")
plt.grid(True)
plt.savefig("phase_stability.png", dpi=300)

plt.figure()
plt.plot(f, d_il)
plt.xlabel("Fréquence [GHz]")
plt.ylabel(r"$\Delta |S_{21}|$ [dB]")
plt.title("Variation de pertes d’insertion sous flexion")
plt.grid(True)
plt.savefig("insertion_loss_variation.png", dpi=300)
```

---

## Rapport de recette à produire

Le rapport Markdown final doit contenir :

1. Identification des cordons : référence, numéro de série, longueur, date de réception.
2. Conditions de mesure : température,  VNA, kit de calibration, date d’étalonnage.
3. Paramètres VNA exacts.
4. Courbes $|S_{21}|$ de 2 à 18 GHz pour les deux cordons.
5. Courbes $|S_{11}|$ et VSWR pour les deux cordons.
6. Phase $S_{21}$, de préférence dé-enroulée.
7. Pertes linéiques estimées :

$$
\alpha(f) =
\frac{IL(f)}{L}
\quad
[\mathrm{dB/m}]
$$

avec $L = 5\ \mathrm{m}$.

8. Variation de phase sous torsion :

$$
\Delta\phi_k(f)
$$

9. Variation de perte sous torsion :

$$
\Delta IL_k(f)
$$

10. Dérive temporelle à 2, 10 et 18 GHz.
11. Conclusion : aptitude ou non des cordons au banc GPR 2–18 GHz.

---

## Grille de validation

| Essai | Résultat à fournir | Validation |
|---|---|---|
| Étalonnage | Fichier `.cal`, vérification Thru et Load | Thru plat, charge bien adaptée |
| Pertes d’insertion | $IL(f)$ pour A et B | Pas de discontinuité anormale |
| ROS | VSWR$f$ pour A et B | Conforme au cahier des charges |
| Réciprocité |$\lvert S_{21} \rvert-\lvert S_{12} \rvert$ | Faible écart |
| Torsion | $\Delta\phi(f)$, $\Delta IL(f)$ | Dérive acceptable pour le GPR |
| Temps | $\Delta\phi(t)$, $\Delta IL(t)$ | Dérive faible et reproductible |
| Retour à référence | T0 final après torsions | Pas d’hystérésis importante |

---

## Annexe A1 : "Cable droit"

## Principe à retenir

* Remplacer la configuration « câble droit » par une **couronne lâche à un seul étage**, posée sur un support non métallique, avec un diamètre et un sens d’enroulement fixes. La référence devient alors :

$$
\text{Configuration } T_0 = \text{couronne lâche reproductible}
$$

et non « câble tendu ».

C’est cohérent avec les pratiques de caractérisation de câbles : les essais de stabilité en phase utilisent un mandrin, une normalisation dans une position initiale, puis une flexion contrôlée d’un tour complet autour du mandrin. Pour les essais de dérive thermique, les normes recommandent également de placer les échantillons en **couronnes lâches**, avec un diamètre au moins égal à 10 fois le rayon minimal statique du câble. 

## Montage recommandé

### Configuration de référence $T_0$

* Utiliser une **grande couronne lâche**, par exemple de diamètre 60 à 100 cm, formée à la main sans torsion.

```text
ZNB Port 1 ── court cordon d’étalonnage ──┐
                                           │
                                  Cordon DUT 5 m
                                           │
ZNB Port 2 ── court cordon d’étalonnage ──┘
```

Le cordon de 5 m est enroulé en une seule couche, sans croisement, sur une table ou un support circulaire.

### Réalisation pratique

1. Marquer au feutre ou au scotch deux repères sur la table : `PORT 1` et `PORT 2`.
2. Placer un cercle guide de diamètre connu, par exemple 80 cm, en bois, PVC ou plastique.
3. Enrouler le câble autour du cercle en une seule couche.
4. Ne tirer jamais sur le câble : il doit reposer naturellement.
5. Fixer la couronne avec 3 attaches Velcro larges, jamais avec des colliers serrés.
6. Laisser environ 30 à 50 cm de câble non enroulé près de chaque connecteur, pour éviter toute contrainte au niveau des SMA.
7. Orienter les connecteurs vers le VNA sans les plier latéralement.
8. Noter le sens d’enroulement : horaire ou antihoraire.
9. Photographier le montage avant chaque mesure.

**Attention :** A la disposition du cable

* Ce qu’il faut faire : une seule couche

```text
Vue de dessus :

        ┌─────────────────────┐
        │   tour 1            │
        │  ┌───────────────┐  │
        │  │   tour 2      │  │
        │  │  ┌─────────┐  │  │
        │  │  │ tour 3  │  │  │
        │  │  └─────────┘  │  │
        │  └───────────────┘  │
        └─────────────────────┘
```

Les spires sont concentriques, mais elles ne se superposent pas verticalement. Le câble reste posé à plat sur la table ou sur le support.

* Ce qu’il faut éviter : plusieurs couches

```text
Vue de côté :

   couche 3 :   ─────────────
   couche 2 :   ─────────────
   couche 1 :   ─────────────
```

Ici, les tours sont empilés. 

Pour une recette, l’objectif n’est pas de ranger joliment le câble, mais d’obtenir une **configuration mécanique reproductible**. Une couronne lâche à une seule couche est donc plus stable et plus facile à décrire. 

### Exemple de géométrie normalisée

| Paramètre | Valeur proposée |
|---|---|
| Diamètre de couronne | 80 cm |
| Nombre de tours | Selon la longueur réelle, environ 2 tours |
| Nombre de couches | 1 uniquement |
| Croisements | Aucun |
| Traction | Nulle |
| Fixation | Velcro large, sans compression |
| Longueur libre près connecteurs | 30 à 50 cm |
| Sens d’enroulement | Toujours identique |

Pour un câble de 5 m et une couronne de diamètre 80 cm, la longueur d’un tour est :

$$
L_{\mathrm{tour}} = \pi D = \pi \times 0,80 \approx 2,51\ \mathrm{m}
$$

Le câble fera donc environ :

$$
N = \frac{5}{2,51} \approx 2\ \text{tours}
$$


## Règle essentielle : rayon de courbure

Avant de fixer le diamètre de couronne, vérifier le **rayon de courbure minimal** indiqué sur la fiche technique du câble. 

Si le fabricant ne donne pas cette valeur, adopte une marge prudente :

$$
R_{\mathrm{couronne}} \geq 10 \times R_{\min,\mathrm{statique}}
$$

Cette règle de marge est notamment utilisée dans les méthodes normalisées d’essai de stabilité de phase des câbles coaxiaux. [standards.iteh](https://standards.iteh.ai/catalog/standards/iec/1f9f1183-3d0c-4552-87e3-328601ddb570/iec-61196-1-111-2024)

---

## Test de torsion adapté

* Ne cherchez pas à tordre tout le câble de 5 m. Isoler une **section centrale contrôlée**.

### Montage

1. Formee la couronne de référence $T_0$.
2. Repèrer une section centrale d’environ 1 m, loin des connecteurs.
3. Placer un mandrin non métallique, par exemple PVC, de rayon connu : 150 mm, 200 mm ou 300 mm.
4. Enrouler uniquement cette section d’un tour complet, soit $360^\circ$.
5. Maintenir le reste du câble exactement dans la même position.
6. Mesurer $S_{21}$, $S_{12}$, $S_{11}$ et $S_{22}$.
7. Revenir à $T_0$ et vérifier le retour à la référence.

Cette méthode correspond aux protocoles industriels : normalisation dans la position initiale, enroulement d’un tour complet autour d’un mandrin, mesure, puis retour à la position initiale et nouvelle normalisation. 

### Configurations recommandées

| Test | Géométrie |
|---|---|
| $T_0$ | Couronne lâche de référence, sans flexion supplémentaire |
| $T_1$ | Section centrale enroulée $360^\circ$, $R=300\ \mathrm{mm}$ |
| $T_2$ | Section centrale enroulée $360^\circ$, $R=200\ \mathrm{mm}$ |
| $T_3$ | Section centrale enroulée $360^\circ$, $R=150\ \mathrm{mm}$, si compatible |
| $T_4$ | Même essai en sens inverse, pour détecter une asymétrie |
| $T_5$ | Retour à $T_0$, mesure de l’hystérésis |

La variation à étudier est alors :

$$
\Delta\phi_k(f)
=
\mathrm{unwrap}\left[\arg S_{21,k}(f)\right]
-
\mathrm{unwrap}\left[\arg S_{21,0}(f)\right]
$$

et pour la réciprocité :

$$
\Delta\phi_{\mathrm{rec},k}(f)
=
\mathrm{unwrap}\left[\arg S_{21,k}(f)\right]
-
\mathrm{unwrap}\left[\arg S_{12,k}(f)\right]
$$

---

## Point important : cordons d’étalonnage

Les cordons courts entre le VNA et les extrémités du cordon de 5 m doivent être :

- Courts : 20 à 50 cm.
- Phase-stables si possible.
- Fixés au banc.
- Jamais déplacés après calibration.
- Protégés de toute traction transmise par le câble de 5 m.


## Conséquence sur la recette

Dans le document, remplacer toutes les occurrences de :

```text
Câble droit, référence
```

par :

```text
Couronne lâche normalisée, diamètre D = 80 cm, une seule couche, sens horaire
```

```

