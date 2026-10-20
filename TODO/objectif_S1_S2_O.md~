# Semaine 1 : première recette du VNA

## Objectifs

### Formation

Etre capable de :

- configurer un canal de mesure ;
- choisir une plage de fréquence ;
- régler le nombre de points, l’IFBW et la puissance ;
- afficher les paramètres $S$ ;
- utiliser les marqueurs ;
- sauvegarder un état et un fichier Touchstone ;

### Contrôle fonctionnel

Le contrôle fonctionnel vérifie que :

- l’appareil démarre correctement ;
- l’auto-test ne signale aucune erreur ;
- les ports RF fonctionnent ;
- la source délivre un signal ;
- les récepteurs mesurent une transmission et une réflexion ;
- les interfaces réseau et SCPI sont accessibles.

---

## Matériel nécessaire

### Instrumentation

- Analyseur de réseau vectoriel R&S ZNB3020.
- Cordon secteur.
- Documentation utilisateur.
- Certificat d’étalonnage de l’appareil.
- Certificat et définition du kit de calibration.
- Ordinateur.

### Chaîne RF

- Deux câbles de test adaptés à la fréquence maximale.
- Kit SOLT adapté au type et au genre des connecteurs.
- Adaptateurs.
- Clé dynamométrique adaptée aux connecteurs.
- Charges 50 Ω.
- Court-circuit.
- Atténuateurs fixes caractérisés.
- Câble ou ligne de longueur connue.
- Antenne destinée au banc GPR.

---

## Sécurité et bonnes pratiques (rappel)

### Protection des ports

Avant toute connexion :

- vérifier l’absence de tension continue ;
- décharger les câbles si nécessaire ;
- vérifier la puissance maximale admissible ;
- ne jamais connecter un signal externe ;

### Connecteurs

- Inspecter les connecteurs avant chaque mesure.
- Tourner uniquement l’écrou du connecteur.
- Utiliser le couple recommandé par le constructeur.
- Éviter les adaptateurs en cascade.
- Ne jamais faire tourner le corps du câble pendant le serrage.

### Câbles

Après calibration :

- ne pas déplacer les câbles ;
- ne pas les plier brusquement ;
- ne pas modifier leur rayon de courbure ;
- immobiliser mécaniquement les câbles sur le banc.

### Stabilisation thermique

Laisser l’appareil atteindre son régime thermique avant :

- une calibration ;
- une mesure de précision ;
- un essai de dérive ;
- une comparaison entre deux configurations.

---

## Métadonnées

**Toute mesure doit être accompagnée des paramètres suivants :**

| Paramètre | Valeur |
|---|---|
| Fréquence de début | |
| Fréquence de fin | |
| Nombre de points | |
| IFBW | |
| Puissance source | |
| Moyennage | |
| Type de balayage | |
| Temps de balayage | |
| Paramètre $S$ | |
| Type de calibration | |
| Plan de référence | |
| Câbles utilisés | |
| Adaptateurs utilisés | |
| Température | |
| Date et heure | |
| Opérateur | |

Une valeur mesurée sans ces informations est difficilement reproductible.

---

# Activité 1 — Réception du VNA

## Réception et identification

### Objectif

Vérifier que l’appareil reçu correspond à la commande et ne présente pas de dommage visible.

### Procédure

1. Photographier l’emballage avant ouverture.
2. Rechercher les chocs, déformations ou traces d’humidité.
3. Comparer le contenu avec le bon de livraison.
4. Relever la référence exacte.
5. Relever le numéro de série.
6. Relever la version du firmware.
7. Relever les options installées.
8. Inspecter le châssis, l’écran, les ventilateurs et les connecteurs RF.
9. Photographier toute anomalie.

### Critère de décision

- **OK** : appareil complet et intact.
- **NOK** : dommage ou élément manquant bloquant l’installation.
- **Réserve** : anomalie mineure documentée et transmise au fournisseur.

### Livrable

- Fiche d’identification.
- Photographies.
- Copie du bon de livraison.
- Liste des accessoires reçus.

## Première mise sous tension

### Objectif

Vérifier le démarrage et l’état général de l’instrument.

### Procédure

1. Installer l’appareil.
2. Mettre l’appareil sous tension.
3. Observer le démarrage du système.
4. Relever les éventuels messages d’erreur.
5. Vérifier l’affichage et les commandes.
6. Relever la date, l’heure et la configuration régionale.
7. Lancer l’auto-test selon le manuel correspondant au firmware.
8. Enregistrer le résultat.

### Critère de décision

Toute erreur de démarrage ou d’auto-test doit être signalée avant de poursuivre.

## Prise en main de l’interface

### Objectif

Comprendre l’organisation d’un VNA avant de connecter un dispositif sous test.

### Procédure

1. Effectuer un preset.
2. Identifier les notions de canal, trace et paramètre.
3. Régler les fréquences de début et de fin.
4. Régler le nombre de points.
5. Régler l’IFBW.
6. Régler la puissance source.
7. Afficher $S_{11}$, $S_{21}$, $S_{12}$ et $S_{22}$.
8. Utiliser les affichages :
   - magnitude en dB ;
   - phase ;
   - phase déroulée ;
   - diagramme de Smith ;
   - affichage polaire ;
   - ROS ;
   - retard de groupe.
9. Placer un marqueur.
10. Utiliser un marqueur delta.
11. Rechercher un maximum ou un minimum.
12. Sauvegarder un état de mesure.
13. Exporter un fichier Touchstone.

### Être capable d’expliquer

- la différence entre un canal et une trace ;
- le rôle de l’IFBW ;

## Contrôle fonctionnel sans calibration

###  Test T1 — Transmission

#### Objectif

Vérifier que la chaîne de transmission entre les deux ports fonctionne.

#### Montage

Relier les ports avec :

- les câbles de test ;
- le thru approprié ;
- l’adaptateur éventuellement nécessaire.

#### Réglages

Documenter la configuration utilisée (cf metadonnées):

- bande de fréquence ;
- nombre de points ;
- IFBW ;
- puissance ;
- moyennage.

#### Observations attendues

On recherche :

- une transmission présente sur toute la bande ;
- une réponse régulière ;
- des pertes compatibles avec les câbles et les adaptateurs ;
- une cohérence générale entre $S_{21}$ et $S_{12}$.

### Test T2 — Charge 50 Ω

#### Objectif

Vérifier la mesure de réflexion.

#### Montage

Réaliser deux essais distincts :

1. charge directement connectée au port ;
2. charge connectée au bout du câble de test.

#### Procédure

1. Mesurer la charge directement connectée.
2. Enregistrer $S_{11}$ ou $S_{22}$.
3. Connecter ensuite la charge au bout du câble.
4. Observer la modification de la trace.
5. Ne pas comparer directement les deux courbes sans tenir compte du plan de référence.

#### Interprétation

La mesure au bout d’un câble comprend les effets :

- de la charge ;
- du câble ;
- des connecteurs ;
- du port du VNA.

### Test T3 — Court-circuit

#### Objectif

Vérifier la réponse d’un court-circuit.

### Test T4 — Comparaison des ports

#### Objectif

Rechercher une anomalie évidente entre les ports.

#### Procédure

1. Mesurer la même charge sur le port 1 puis sur le port 2.
2. Utiliser la même configuration.
3. Comparer les courbes.
4. Documenter l’écart observé.

#### Limite

Une différence entre les ports ne signifie pas nécessairement qu’un port est défectueux. Elle peut provenir :

- de deux câbles différents ;
- de deux adaptateurs différents ;
- d’une connexion différente ;
- de la charge ;
- de la répétabilité du montage.

---

# Activité 2 — Calibration et vérification de performance

##  Préparation de la calibration

### Procédure

1. Mettre le VNA sous tension suffisamment longtemps pour atteindre un régime stable.
2. Vérifier la fréquence maximale du kit.
3. Importer ou sélectionner la définition correcte du kit.
4. Définir la configuration de mesure.
5. Ne plus modifier la bande, le nombre de points ou les paramètres essentiels après calibration sans vérifier la validité de la calibration.

## Calibration SOLT deux ports

### Objectif

Déplacer le plan de référence au bout des câbles de test et corriger les erreurs systématiques de la chaîne (calibration full two port).

### Procédure générale

1. Créer la configuration de mesure.
2. Sélectionner une calibration deux ports.
3. Sélectionner la méthode SOLT.
4. Sélectionner la définition du kit.
5. Appliquer la calibration.
6. Sauvegarder l’état et la calibration.

### Informations à consigner

- Référence du kit.
- Numéro de série du kit.
- Type de connecteur.
- Genre des connecteurs.
- Type de thru.
- Utilisation ou non d’adaptateurs.
- Fréquence de début et de fin.
- Nombre de points.
- IFBW.
- Puissance.
- Date et heure.
- Opérateur.

## Vérification de la calibration

La vérification ne consiste pas à reconnecter immédiatement les mêmes étalons utilisés pour la calibration. Elle doit utiliser des dispositifs de contrôle indépendants lorsque cela est possible.

### Charge

Mesurer une charge (de précision) non utilisée pour la calibration.

Documenter :

- $S_{11}$ ou $S_{22}$ ;
- l’écart mesuré ;
- la configuration ;
- la répétabilité de connexion.

### Atténuateur connu

Mesurer un atténuateur connu.

Comparer :

$$ \Delta A(f)=A_{\text{mesuré}}(f)-A_{\text{certificat}}(f).  $$

L’écart acceptable doit être défini à partir :

- du certificat de l’atténuateur ;
- de la précision annoncée du VNA ;
- de la configuration ;
- de l’incertitude recherchée.

### Répétabilité de connexion

1. Mesurer l’atténuateur.
2. Déconnecter l’atténuateur.
3. Inspecter la connexion.
4. Reconnecter au couple recommandé.
5. Répéter la mesure au moins trois fois.
6. Comparer les résultats.

La dispersion observée représente notamment :

- la répétabilité mécanique ;
- la sensibilité du connecteur ;
- la stabilité du câble ;
- le bruit de mesure.

### Câble de longueur connue

Mesurer le câble.

Comparer :

- la pente de phase ;
- le retard de groupe ;
- la perte d’insertion ;
- la réponse en fréquence.

---

# Activité 3 — Premiers essais de performance

## Lire un article de référence

* lire [dl.cdn-anritsu](https://dl.cdn-anritsu.com/en-us/test-measurement/files/Application-Notes/Application-Note/11410-00724D.pdf)

##  Test P1 — Bruit de Trace (trace noise)

> **Trace Noise (High Level Noise)** - This is a measure of the scatter of data when measuring a high-level signal (full reflect or transmission through a short transmission line). The measurement is specified at default power with a 1 kHz IFBW and default auto-reduction for frequencies below 3 MHz. The measurement is performed by acquiring a minimum of 10 sweeps of data from the desired parameter, in linear magnitude and phase, after a trace-math normalization. At each frequency point, the population-based standard deviation is computed. This forms the RMS high-level noise number. For magnitude, this is normally converted back to log magnitude.

On estime le **bruit de trace** à partir de la variation de la mesure du VNA lui-même

### Montage proposé

Le montage est :

```text Port 1 ─── câble de test ─── thru ─── câble de test ─── Port 2 ```

Conditions :

- câbles immobilisés ;
- connecteurs correctement serrés ;
- calibration active ;
- aucune modification mécanique pendant l’acquisition ;
- mesure de $S_{21}$, généralement en complexe (partie réelle et imaginaire)

Le thru fournit un signal relativement fort et stable. On mesure donc principalement la variation propre à la chaîne de réception, plutôt que le niveau très faible du plancher de bruit.

### Procédure

Pour une valeur d’IFBW donnée, par exemple $1\ \mathrm{kHz}$ :

1. Réaliser le montage proposé.
2. Faire un Preset sur le VNA
2. Régler le nombre de points à 51.
3. Régler la fréquence entre 2 GHz et 18 GHz
4. Régler l’IFBW à $1\ \mathrm{kHz}$.
5. Désactiver le moyennage ou fixer explicitement son facteur à 1.
6. Effectuer une calibration adaptée.
7. Afficher le $S_{21}$ et le $S_{12}$.
8. Lancer un premier balayage.
9. Enregistrer les valeurs complexes dans un fichier Touchstone bruit_trace_IFBW_1KHz_n_1.s2p (pour le premier balayage, n_2 pour le second et ainsi de suite)
10. Répéter 20 fois les étapes 8 et 9 sans modifier le montage.
11. Réaliser le traitement mathématique proposée ci dessous (en python avec [scikit_rf](https://scikit-rf.readthedocs.io/en/latest/) pour lire les fichier Touchstone)
12. Recommencer pour d’autres IFBW (sans refaire la calibration).
13. Rédiger un compte rendu avec une analyse (penser à relever l'ensemble du setup de l’analyseur).

Les IFBW peuvent être choisies, par exemple :

$$ 100\ \mathrm{Hz},\quad 1\ \mathrm{kHz},\quad 10\ \mathrm{kHz}.  $$

La réduction de l’IFBW diminue généralement le bruit, mais augmente le temps de balayage.

### Traitement

Le VNA fournit :

$$ S_{21}=a+jb, $$

l'amplitude en dB est :

$$ S_{21,\mathrm{dB}} = 20\log_{10}\left|S_{21}\right| =20\log_{10}\left(\sqrt{a^2+b^2}\right).  $$

La phase vaut :

$$ \varphi=\arg(S_{21}).  $$

#### Méthode de calcul

Soit $x_{k,i}$ la valeur mesurée au point fréquentiel $k$ lors du balayage $i$.

**Bruit de trace d'amplitude**

Pour chaque fréquence $f_k$, calculer :

$$ \sigma_A(f_k) = \sqrt{ \frac{1}{N-1} \sum_{i=1}^{N} \left[A_i(f_k)-\overline{A}(f_k) \right]^2 }.  $$

On obtient une courbe :

$$ \sigma_A(f) $$

exprimée en dB RMS.

**Bruit de trace de phase**

Pour la phase, il faut d’abord éviter les sauts de $+180^\circ$ à $-180^\circ$. Il faut donc dérouler la phase avant de calculer l’écart-type :

$$ \sigma_\varphi(f_k) = \sqrt{ \frac{1}{N-1} \sum_{i=1}^{N} \left[\varphi_i(f_k)-\overline{\varphi}(f_k) \right]^2 }.  $$

Le résultat est exprimé en degrés RMS.

### Ce qu'il faut tracer

Pour chaque IFBW, tracer :

1. les 20 traces de $S_{21}$ ;
2. la trace moyenne ;
3. l’écart-type en fonction de la fréquence ;
4. éventuellement le bruit maximal et moyen.
5. faire de même pour le $S_{12}$

Exemple de tableau de synthèse :

| IFBW | Temps de balayage | Bruit RMS moyen | Bruit RMS maximal |
|---:|---:|---:|---:|
| 100 Hz | | | |
| 1 kHz | | | |
| 10 kHz | | | |

On peut aussi tracer :

$$ \sigma_A \quad \text{en fonction de} \quad \mathrm{IFBW}.  $$

## Test P2 — Estimation du bruit de mesure

> **Noise Floor :** This is a measure in **absolute power (dBm)** of the noise floor of the system, referenced to the test port. Typically, this is calculated by measuring **S21** and **S12** with a **short-thru line** connected and the port power set to some value $X$. The cable loss is normally subtracted separately or, alternatively, a **flat-power calibration** can be performed at the end of the cable. The traces are normalized with this *thru* in place. The ports are then terminated with **loads** (typically), and **S21** and **S12** are measured in a **10 Hz bandwidth**, with no averaging. A minimum of **10 sweeps** are acquired in **linear magnitude mode**, and the **root-mean-square (RMS)** value is computed at each frequency point individually. This result is then normally converted back to **log magnitude**.

###  Principe de la mesure

La mesure se déroule en deux étapes.

#### Étape A — Établir une référence de transmission

On connecte une liaison thru courte et à faibles pertes :

```text Port 1 ───── câble de test ───── Port 2 ```

#### Étape B — Mesurer le bruit résiduel

On remplace la liaison entre les ports par des charges adaptées :

```text Port 1 ─── câble de test ─── charge 50 Ω```

```Port 2 ─── charge 50 Ω ```

La transmission directe entre les deux récepteurs est alors supprimée. Le niveau mesuré correspond au bruit résiduel, auquel peuvent s’ajouter les fuites entre les voies.

#### Conditions de mesure

Les conditions suivantes doivent être imposées :

| Paramètre | Valeur recommandée |
|---|---:|
| IFBW | $10\ \mathrm{Hz}$ |
| Moyennage | Désactivé |
| Puissance de port | 0 dBm |
| Nombre de balayages | 20 |
| Mode d’affichage | Magnitude linéaire |
| Paramètres mesurés | $S_{21}$ puis $S_{12}$ |
| Calibration | 2 ports transmission |
| Terminaisons | Charges adaptées de précision |
| Fréquence min. | 2 GHz |
| Fréquence max. | 18 GHz |
| Nombre de points | 2001 |

#### Démarche

1. Effectuer un **Preset du VNA**.
2. Régler le **configuration du VNA**.
3. Connecter un **câble thru** au **port 1**, puis régler l’affichage sur $S_{21}$ et **Magnitude linéaire**.
4. Régler la **puissance du port 1** à **0 dBm**.
6. Effectuer une **calibration 2 ports en transmission uniquement**.
7. Déconnecter le câble du **port 2**. Terminer à la fois le **câble** et le **port 2** avec des **charges** provenant du kit de calibration.
8. Acquérir les données de la trace **20 fois** et calculer, pour chaque point, la **valeur RMS** sur un échantillon de taille 20.
9. Calculer le **bruit de plancher** (*Noise Floor*).
10. Refaire la même démarche pour le $S_{12}$.
11. Comparer la réponse $S_{12}$ à la réponse $S_{21}$.
12. Faire un CR et analyser les résultats

#### Formulation théorique

À chaque balayage, enregistrer la valeur pour chacun des $N_f$ points fréquentiels (fichier Touchstone).

On note :

$$ x_{i,k} $$

la valeur mesurée au balayage $i$, à la fréquence $f_k$.

Le tableau de données possède alors la forme :

$$ \mathbf{X} = \begin{bmatrix} x_{1,1} & x_{1,2} & \cdots & x_{1,N_f}\\
x_{2,1} & x_{2,2} & \cdots & x_{2,N_f}\\ \vdots & \vdots & \ddots & \vdots\\
x_{N_{\mathrm{sw}},1} & x_{N_{\mathrm{sw}},2} & \cdots &
x_{N_{\mathrm{sw}},N_f} \end{bmatrix}.  $$

Chaque colonne correspond à une fréquence. Le calcul RMS est effectué séparément pour chaque colonne.

La procédure demande un calcul RMS en mode magnitude linéaire. Il faut donc éviter de calculer directement une moyenne RMS sur les valeurs en dB.

Pour une valeur $S_{21}$, la magnitude linéaire est :

$$ a_{i,k}=|S_{21,i}(f_k)|.  $$

Le calcul RMS, à chaque fréquence $f_k$, est :

$$ a_{\mathrm{RMS}}(f_k) = \sqrt{ \frac{1}{N_{\mathrm{sw}}}\sum_{i=1}^{N_{\mathrm{sw}}} a_{i,k}^{2} }.  $$

Cette opération est réalisée indépendamment pour chaque fréquence.

Une fois la valeur RMS obtenue, la convertir en dB de rapport de puissance :

$$ L_{\mathrm{RMS}}(f_k) = 20\log_{10} \left( a_{\mathrm{RMS}}(f_k) \right).$$

La valeur obtenue est une grandeur logarithmique de type transmission.

Pour exprimer ce résultat en puissance absolue référencée au port, il faut connaître la puissance de référence $P_{\mathrm{ref}}$.

Si la puissance de port est $P_{\mathrm{port}}$, alors :

$$ P_{\mathrm{noise,dBm}}(f_k) = P_{\mathrm{port,dBm}}
+
L_{\mathrm{RMS}}(f_k).  $$

Exemple :

$$ P_{\mathrm{port}}=-10\ \mathrm{dBm} $$

et :

$$ L_{\mathrm{RMS}}=-105\ \mathrm{dB}.  $$

Alors :

$$ P_{\mathrm{noise,dBm}} = -10-105 = -115\ \mathrm{dBm}.  $$

#### Résultats à présenter

Le rapport doit contenir :

1. une photo du montage thru ;
2. une photo du montage avec charges ;
3. la configuration du VNA ;
4. la référence de calibration ;
5. les valeurs brutes des balayages ;
6. le calcul RMS point par point ;
7. la courbe $S_{21}$ en dBm ;
8. la courbe $S_{12}$ en dBm ;
9. la comparaison avec la fiche technique ;
10. les écarts et les résultats d’analyse ;

