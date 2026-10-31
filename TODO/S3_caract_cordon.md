# Caractérisation de deux cordons SMA 5 m — Banc GPR 2–18 GHz

*F. D. Dernière modification : 30 octobre 2026*

## Objectifs

* Caractériser les deux cordons coaxiaux SMA de 5 m destinés au radar GPR Heat Coffee, sur la bande utile **2–18 GHz**. 
* Grandeurs mesurées : $S_{11}$, $S_{22}$, ROS, $S_{21}$, $S_{12}$ (module et phase), stabilité de phase et de module en flexion et en mouvement, dérive temporelle et thermique, appariement des deux cordons.

## Critères d'acceptation

Bande d'évaluation : 2–18 GHz, sauf mention contraire.

| ID | Grandeur | Seuil | Origine du seuil |
|---|---|---|---|
| EXG-01 | Pertes d'insertion $IL(f)=-20\log_{10}\lvert S_{21}\rvert$ | $\le IL_{\text{fiche}}(f)+[m_{IL}]$ dB (*proposé* : 0,5 dB) | Fiche constructeur |
| EXG-02 | Régularité de $IL$ : écart à l'ajustement $a\sqrt f + bf + c$ | $\le [0{,}3]$ dB crête (*proposé*) | À valider |
| EXG-03 | ROS de $S_{11}$ et de $S_{22}$ | $\le 1{,}5$ sur $\ge [90]$ % de la bande et $\le [2{,}0]$ partout (*proposé*) ; $1{,}5 \Leftrightarrow RL \approx 14$ dB | Fiche Constructeur (1.5=exemple) |
| EXG-04 | Répétabilité de connexion, $N \ge 10$ | $\lvert\Delta S_{21}\rvert \le 0{,}05$ dB crête ; $\Delta\phi \le [1^\circ]$ à 18 GHz (*proposé*) | |
| EXG-05 | Réciprocité $\Delta IL_{\text{rec}}$ et $\Delta\phi_{\text{rec}}$ |  |  | 
| EXG-06 | Variation de phase en flexion, $\max_f \lvert\Delta\phi_k(f)\rvert$ | $\le \Phi_{\text{flex}}(f)$ = 5 deg. | Budget GPR |
| EXG-07 | Variation de module en flexion | $\le [0{,}1]$ dB (*proposé*) |   |
| EXG-08 | Hystérésis : écart de retour à $T_0$ après flexion | $\le$ 10 deg. | Budget GPR |
| EXG-09 | Stabilité dynamique (essai CW en mouvement), crête-à-crête | $\Delta\phi_{pp} \le$ 10 deg. | Budget GPR |
| EXG-10 | Dérive sur 2 h  | $\lvert\Delta\phi\rvert \le$ 10 deg. | Budget GPR |
| EXG-11 | Appariement A/B : $\Delta IL$, phase résiduelle  | $\le$ 0.1 dB,  $\le$ 5 deg. | Budget GPR |


## Matériel

| Équipement | Spécification | N° d'inventaire / date d'étalonnage |
|---|---|---|
| VNA | R&S ZNB3020, 2 ports, 9 kHz–20 GHz  | [ ] |
| Cordons à caractériser | Câble A, Câble B, 5 m, SMA, DC–20 GHz | SN [ ] |
| Kit d'étalonnage | Compatible avec les connecteurs des cordons d'étalonnage, caractérisé jusqu'à 20 GHz  | [ ] |
| Cordons d'étalonnage | 2 cordons courts (20 à 50 cm), fixés au banc | [ ] |
| Étalons de vérification **indépendants** | atténuateur (par ex. 10 dB), charge et court-circuit d'un autre jeu | [ ] |
| Adaptateurs SMA |  Références et genres consignés | [ ] |
| Clé dynamométrique SMA | Couple SMA : typ. 0,56 N·m (5 in·lb). Ne pas appliquer 0,9 N·m (interface 3,5 mm) à un SMA | [ ] |
| Thermomètre |  air ambiant et contact sur la couronne ; résolution $\le$ 0,1 °C, incertitude indiquée | [ ] |
| Tambour de couronne | Non métallique, diamètre à calculer | — |
| Mandrins | Non métalliques, rayons (300,200,150 mm) | — |
| PC | Pilotage SCPI, scripts d'acquisition et de traitement versionnés | [ ] |

## Données constructeurs cordons (si disponibles)

À renseigner.

| Donnée | Valeur |
|---|---|
| Rayon de courbure minimal statique $R_{\min,s}$ | [ ] mm |
| Rayon de courbure minimal dynamique $R_{\min,d}$ | [ ] mm |
| Diamètre extérieur du câble $d_c$ | [ ] mm |
| Facteur de vélocité | [ ] |
| Pertes d'insertion annoncées (2, 6, 10, 14, 18 GHz) | [ ] dB |
| Diélectrique (PTFE, autre) | [ ] |

**Rayons de mandrin.** Retenir les rayons de l'ensemble {300, 200, 150} mm qui sont $\ge R_{\min,d}$. Tout essai à un rayon inférieur à $R_{\min,d}$ est interdit. Si $R_{\min,d} > 150$ mm, le test $T_3$ est supprimé. Le rayon utilisé dans les calculs est celui de l'**axe du câble** : $R_k = R_{\text{mandrin}} + d_c/2$.



## Conditions environnementales

- Température de la salle : relevée en début et en fin de manipulation.  
- Banc sous tension $\ge 1$ h ; cordons dans la salle $\ge [2]$ h (*proposé*, la couronne a une inertie thermique non négligeable).
- Aucun mouvement de câble ni de personnel à proximité du banc pendant une acquisition ; pas de courant d'air direct sur les cordons.


## Préparation 

1. Identifier chaque cordon (`CABLE_A_SNxxx`, `CABLE_B_SNxxx`) et photographier les connecteurs.
2. Inspecter les connecteurs : pin non plié, pas de rayure ni de saleté sur le diélectrique, écrou libre. 
3. Décharger les cordons (ESD) avant chaque connexion au VNA.
4. Serrer **tous** les raccords à la clé dynamométrique, au couple de l'interface.
5. Fixer les cordons d'étalonnage au banc (collier large, sans compression) ; ils ne bougeront plus de toute la session.

## Configuration du VNA 

Une seule configuration est utilisée pour l'étalonnage et toutes les mesures statiques ; toute modification impose de réétalonner.

| Paramètre | Valeur |
|---|---|
| Bande d'acquisition | 2 à 18 GHz  |
| Nombre de points | 8001  |
| Balayage | Linéaire en fréquence |
| Puissance de source | 0 dBm |
| Bande IF | 1 kHz |
| Moyennage | Aucun (à augmenter si l'essai l'exige) |
| Correction | Full 2-port (SOLT / TOSM) |
| Formats | $S_{21}$ : dB + phase ; $S_{11}$ : dB, Smith, ROS |
| Sauvegarde | `.s2p` + état VNA + capture d'écran |

* Étalonnage **full 2-port SOLT** (nommé TOSM sur le ZNB). Le plan de référence est situé aux **extrémités des cordons d'étalonnage**, aux points où le cordon de 5 m sera connecté.

### Vérification avec étalons indépendants (V1)

La remesure du thru et de la charge utilisés pour calibrer n'est **pas** une vérification. Utiliser des étalons distincts :

| Contrôle | Étalon | Critère |
|---|---|---|
| V1a | Atténuateur [10] dB | $\lvert S_{21}\rvert$ conforme à la valeur certifiée à $\pm [\ ]$ dB ; phase sans saut |
| V1b | Charge et court-circuit d'un autre jeu | $\lvert S_{11}\rvert$ cohérent avec valeur attendue du kit (valeur kit : [ ] dB) |

Enregistrer les résultats de V1 (fichiers `.s2p`).

### Contrôle de fin de campagne (V2)

À la fin de chaque session : remesurer l'étalon V1a et un thru direct (sans DUT). 

> Les cordons d'étalonnage ne doivent jamais être tordus ni déplacés après calibration, sinon la correction est invalide.

## Montage de référence $T_0$ : couronne sur tambour

* Utiliser une **grande couronne lâche**, par exemple de diamètre 60 à 100 cm, formée à la main sans torsion.

```text
ZNB Port 1 ── court cordon d’étalonnage ──┐
                                           │
                                  Cordon DUT 5 m
                                           │
ZNB Port 2 ── court cordon d’étalonnage ──┘
```

Le cordon de 5 m est enroulé en une seule couche, sans croisement, sur une table ou un support circulaire.

#### Réalisation pratique

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

#### Exemple de géométrie normalisée

| Paramètre | Valeur proposée |
|---|---|
| Diamètre de couronne | 80 cm |
| Nombre de tours | Selon la longueur réelle, environ 2 tours |
| Nombre de couches | 1 uniquement |
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


### Règle essentielle : rayon de courbure

Avant de fixer le diamètre de couronne, vérifier le **rayon de courbure minimal** indiqué sur la fiche technique du câble. 

Si le fabricant ne donne pas cette valeur, adopte une marge prudente :

$$
R_{\mathrm{couronne}} \geq 10 \times R_{\min,\mathrm{statique}}
$$

## Plan des essais

L'ordre est imposé : il établit d'abord ce que le banc sait mesurer, puis ce que fait le cordon.

| Étape | Essais |  Pourquoi dans cet ordre |
|---|---|---|
| 0 | Préparation, étalonnage, vérification V1 |  Base de la session |
| 1 | **Plancher** P1 à P4 | Sans plancher, aucune variation observée n'est attribuable au cordon |
| 2 | Statique S1 et S2, réciprocité | Caractéristique de référence de chaque cordon |
| 3 | Flexion M1 |  Essais mécaniques, hystérésis incluse |
| 4 | Dynamique M2 |  Représentatif du fonctionnement du GPR |
| 5 | Dérive D1 (et D2 en option) |  Longue durée, enregistrement automatique |
| 6 | Contrôle V2 de fin de session | Détecte la dérive de calibration |
| 7 | Appariement A/B et rapport | Exploitation |

Les cordons A et B suivent la **même** séquence, dans la même session si possible (sinon, après réétalonnage, avec nouvel essai P3).

---

## Essais « plancher » (P1 à P4)

Ces essais caractérisent le banc, pas le cordon. Le plancher retenu pour chaque grandeur est le **maximum** des valeurs P1 à P4 ; il sert à décider si une variation observée plus tard est significative.

| Essai | Objet | Protocole | Grandeurs relevées |
|---|---|---|---|
| **P1** Bruit de trace | Bruit de trace | Cordon A en $T_0$, 2 balayages consécutifs sans rien toucher, répéter 10 fois | Écart-type de $\lvert S_{21}\rvert$ (dB) et de la phase (°), à 2, 4, 6, 8, 10, 12, 14, 16, 18 GHz. Cible *proposée* : $< 0{,}005$ dB et $< 0{,}05^\circ$. Sinon, réduire la bande IF ou moyenner, puis réétalonner |
| **P2** Répétabilité de connexion | Connecteurs | Déconnecter et reconnecter les **deux** extrémités du cordon, au couple, $N \ge 10$ ; couronne non touchée | Écart-type et crête de $\lvert\Delta S_{21}\rvert$, de $\Delta\phi$ et de $\lvert\Delta S_{11}\rvert$, aux 9 fréquences |
| **P3** Reproductibilité de $T_0$ | Montage | Défaire et refaire la couronne $N \ge 5$ fois, connecteurs non touchés | Mêmes grandeurs que P2 |
| **P4** Dérive instrumentale | VNA + cordons d'étalonnage | **Thru direct** (sans DUT), 2 h, 1 balayage par minute, automatisé, températures relevées | $\Delta\phi(t)$ et $\Delta\lvert S_{21}\rvert(t)$ aux 9 fréquences |


## Mesures statiques (S1 et  S2)

### Procédure S1

Pour chaque cordon, en configuration $T_0$ :

1. Insérer le DUT entre les deux cordons d'étalonnage, serrage au couple, extrémités libres alignées.
2. Acquérir $S_{11}, S_{21}, S_{12}, S_{22}$. 
3. Sauvegarder :

```text
CABLE_A_SNxxx_T0_S1_YYYYMMDD_hhmm.s2p
CABLE_B_SNxxx_T0_S1_YYYYMMDD_hhmm.s2p
```

### Grandeurs extraites

| Grandeur | Définition | Remarque |
|---|---|---|
| Pertes d'insertion | $IL(f) = -20\log_{10}\lvert S_{21}\rvert$ | Positive en dB |
| Pertes linéiques | $\alpha(f) = IL(f)/L$ en dB/m | Valeur brute, incluant les connecteurs  |
| $S_{11}$, $S_{22}$ | module en dB, ROS  |  |


### Réciprocité (S2)

Pour un cordon passif, $S_{21}$ et $S_{12}$ doivent être égaux. On calcule :

$$
\Delta IL_{\text{rec}}(f) = 20\log_{10}\lvert S_{21}\rvert - 20\log_{10}\lvert S_{12}\rvert,
\qquad
\Delta\phi_{\text{rec}}(f) = \arg\!\left(\frac{S_{21}}{S_{12}}\right)
$$

Le calcul de $\arg(S_{21}/S_{12})$ évite tout dé-enroulement et toute ambiguïté de $2\pi$.

| Grandeur | Critère | Interprétation |
|---|---:|---|
| $\lvert\Delta IL_{\text{rec}}\rvert$ | $< 0{,}05$ dB | Très bonne cohérence |
| $\lvert\Delta IL_{\text{rec}}\rvert$ | $0{,}05$ à $0{,}10$ dB | Acceptable, à surveiller |
| $\lvert\Delta IL_{\text{rec}}\rvert$ | $> 0{,}10$ dB | Problème probable (étalonnage, connecteur, mesure) |
| $\lvert\Delta\phi_{\text{rec}}\rvert$ | $< 1^\circ$ | Très bonne cohérence |
| $\lvert\Delta\phi_{\text{rec}}\rvert$ | $1^\circ$ à $3^\circ$ | Acceptable |
| $\lvert\Delta\phi_{\text{rec}}\rvert$ | $> 3^\circ$ | Vérifier étalonnage, serrage, stabilité mécanique |

### Ajustement des pertes

Ajuster, par moindres carrés sur 2–18 GHz :

$$
IL(f) \approx a\sqrt f + b\,f + c
$$

- $a\sqrt f$ : pertes conducteur ; $b f$ : pertes diélectriques ; **$c$ : contribution des connecteurs et des désadaptations** (valeur à comparer à celle de deux connecteurs seuls).
- L'écart résiduel $IL(f) - \text{ajustement}$ sert à EXG-02 (régularité : l'écart exprime les ondulations et résonances).

---

## Flexion (M1) 

### Séquence de flexion M1

* Rayons $R_k \in \{300, 200, 150\}$ mm, par ordre de sévérité croissante. Pour chaque rayon, trois cycles :

$$
T_0 \rightarrow T_k^{+} \rightarrow T_0 \rightarrow T_k^{-}
$$

où $T_k^{\pm}$ désigne le tour de flexion enroulé sur le mandrin dans un sens ou dans l'autre. Une dernière mesure $T_0$ est faite en fin de série.

1. Placer le cordon en $T_0$, acquérir.
2. Faire passer le tour de flexion sur le mandrin $R_k$, **sans traction**, le reste du montage inchangé.
3. Attendre 30 s, puis acquérir **deux balayages consécutifs** : on retient le second ; l'écart entre les deux est un indicateur de relaxation.
4. Revenir en $T_0$ en suivant le même protocole.
5. Photographier le montage à chaque changement de configuration.

Nom de fichier : `CABLE_A_SNxxx_T1_R300_plus_cycle2_YYYYMMDD_hhmm.s2p`.

### Analyse

- Variation de phase relative à la mesure $T_0$ **précédente** et à la mesure $T_0$ **initiale** :

$$
\Delta\phi_k(f) = \arg\!\left[\frac{S_{21,k}(f)}{S_{21,0}(f)}\right]
$$

(rapport complexe : pas de dé-enroulement séparé ; si la valeur approche $\pm\pi$, dé-enrouler en partant de la plus basse fréquence).
- Variation de retard : $\Delta\tau_k(f) = -\dfrac{1}{2\pi}\dfrac{d\,\Delta\phi_k}{df}$.
- Longueur électrique équivalente (espace libre) : $\Delta L_{\text{éq}}(f) = -\dfrac{c}{2\pi f}\,\Delta\phi_k(f)$. 
- Variation de module : $\Delta\lvert S_{21}\rvert_k = 20\log_{10}\dfrac{\lvert S_{21,k}\rvert}{\lvert S_{21,0}\rvert}$.
- **Hystérésis** : écart entre un $T_0$ de retour et le $T_0$ initial.
- **Dissymétrie** : écart entre $T_k^{+}$ et $T_k^{-}$.
- Statistique sur les trois cycles : moyenne, écart-type, valeur maximale sur 2–18 GHz et aux fréquences (2, 4, 6, 8, 10, 12, 14, 16, 18 GHz).


Sorties : $\Delta\phi_k(f)$, $\Delta\tau_k(f)$, $\Delta L_{\text{éq}}(f)$, $\Delta\lvert S_{21}\rvert_k(f)$, pour chaque $R_k$ et chaque sens.


## Essai dynamique en CW (M2)

Les balayages (quelques dizaines de secondes) ne permettent pas de voir ce que voit le radar quand le câble bouge. L'essai dynamique est le plus représentatif.

**Protocole.**

1. VNA en mode **CW** ($S_{21}$) à 2, 10 et 18 GHz (en option : faire un pas de 2 GHz), bande IF 10 kHz, au moins un point toutes les 10 ms ; fréquences choisies sur des points de la grille d'étalonnage. Les variations étant relatives, l'étalonnage est appliqué si disponible.
2. Deux phases de 60 s, enregistrées en continu :
   - **repos** (câble immobile) : plancher dynamique ;
   - **mouvement imposé** : ondulation de la section centrale de $\pm 30$ cm à environ 1 Hz, sans dépasser $R_{\min,d}$ ;
3. Traitement : $\Delta\phi(t) = \arg[S_{21}(t)/S_{21}(t_0)]$ et $\Delta IL(t)$ ; valeurs crête-à-crête, écart-type, densité spectrale.

## Dérive temporelle et thermique (D1, D2)

### D1 — dérive à température ambiante

1. Cordon en $T_0$, mesure **automatisée** (SCPI) : un balayage par minute pendant $\ge 2$ h.
2. Si Possible -> Enregistrer en continu : température de l'air, **température de contact sur la couronne** (thermocouple collé) ; température du châssis du VNA si accessible.
3. Calculer $\Delta\phi(t)$ et $\Delta\lvert S_{21}\rvert(t)$ aux cinq fréquences, et comparer à P4.
4. Si température disponible, réaliser la corrélation avec la température.


### D2 — essai thermique (option)

Si le GPR est exposé à des variations de température : étuve, rampe lente, cordon en $T_0$, mesure en continu. Couvrir la plage d'emploi, et en particulier la transition connue des PTFE vers 19 °C (à confirmer pour le diélectrique du cordon). Résultat : coefficient de phase en ppm/°C par fréquence.

---

## Appariement des deux cordons A et B

Le radar utilise deux cordons dont les différences se retrouvent dans la chaîne. À partir des mesures S1 et M1 :

| Grandeur | Définition | Critère |
|---|---|---|
| $\Delta IL_{A-B}(f)$ | $IL_A(f) - IL_B(f)$ | EXG-11 |
| $\Delta\tau_{A-B}$ | Différence des retards moyens | EXG-11 |
| Écart de comportement en flexion | Différence des $\Delta\phi_k$ de A et B | Informatif |

