# Compte rendu – Activité 1 : Réception du VNA

**Nom(s) :** Habary Baptiste **Date :** 26/10/2026 **Lieu / banc :** ENS Paris Saclay / Salle S88

---

## 1. Réception et identification

**Objectif :** vérifier que l’appareil reçu correspond à la commande et ne présente pas de dommage visible.

### 1.1 Emballage et contenu

| Point de contrôle | Constat | Photo n° |
| --- | --- | --- |
| État de l’emballage avant ouverture (chocs, déformations, humidité) | Aucun choc détecté, l’appareil à été bien protégé&#32; | 1 à 3 |
| Contenu conforme au bon de livraison ? | Oui le contenu est bien conforme au bon de livraison | Rhode\_et\_Schwarz\_Heat-Coffee\_Bulletin\_de\_livraison\_05-05-2026.pdf |
| Inspection du châssis | RAS | 4 et 5 |
| Inspection de l’écran | RAS | 6 |
| Inspection des ventilateurs | RAS | / |
| Inspection des connecteurs RF | RAS | 7 |
| Autres anomalies | Aucune anomalie détecté | / |

### 1.2 Fiche d’identification

| Information | &#32;VNA | Capture d’écran&#32; |
| --- | --- | --- |
| Constructeur / modèle | R&S |   Instrument Information. HTML |
| Référence exacte | ZNB3020 with 2 ports |  |
| Numéro de série | 100150 |  |
| Version du firmware | 4.12 |  |
| Options installées | ZNB3-B22 | Option VNA. HTML |

### 1.3 Accessoires reçus

| Accessoire | Quantité | État |
| --- | --- | --- |
| Kit de Calibration | 1 | Neuf |
| Guide de démarrage | 1 | Neuf |

### 1.4 Décision de réception

Trois décisions sont possibles :

- **OK** : appareil complet et intact ;
- **NOK** : dommage ou élément manquant bloquant l’installation ;
- **Réserve** : anomalie mineure documentée et transmise au fournisseur.

**Décision retenue **** ****:**** **OK

**Justification :** L'appareil n'as pas de déformation, le carton est bien conforme au bon de commande et aucune anomalie a été detecté.

---

## 2. Première mise sous tension

**Objectif :** vérifier le démarrage et l’état général de l’instrument.

| Point de contrôle | Constat | Photo |
| --- | --- | --- |
| Démarrage du système&#32; | L'appareil s'allume rapidement |     Selftest VNA.HTML |
| Messages d’erreur éventuels | aucun message d'erreur ne s'affiche au démarrage&#32; |  |
| Affichage et commandes | les commandes sont fonctionnels&#32; |  |
| Date / heure | 8:41:07 AM |  |
| Configuration régionale | UTC ( *Coordinated Universal Time*) |  |
| Résultat de l’auto-test | Reussi ( Pass) |  |

---

## 3. Prise en main de l’interface

**Objectif :** comprendre l’organisation d’un VNA avant de connecter un dispositif sous test.

### 3.1 Réglages de base

| Réglage | Valeur utilisée | Chemin dans le menu |
| --- | --- | --- |
| Preset | Fait | Bouton Vert de l'appareil nommé "**Preset**"se trouvant dans l'onglet **Syst****è****me** |
| Fréquence de début | 2 GHz | Bouton** Start**** **de l'appareil  l'onglet **S****t****i****m****u****l****u****s** |
| Fréquence de fin | 18 GHz | Bouton** S****t****o****p**** **de l'appareil  l'onglet **Stimulus** |
| Nombre de points | 4001 | Bouton** S****w****e****e****p**** **de l'appareil  l'onglet **C****ha****n****n****e****l** |
| IFBW | 1 kHz | Bouton** ****P****OWE****R**** ****B****V**** ****A****v****g**** **de l'appareil  l'onglet **Channel**** **puis selectionner l'onglet** ****B****a****nd****-****w****ith** |
| Puissance source | 0 dBm | Bouton** POWER BV Avg **de l'appareil  l'onglet **Channel** |

### 3.2 Notions de canal, trace, paramètre

- Un **canal** est un **réglage de mesure** : la bande de fréquence, le nombre de points, l’IFBW, la puissance source, le moyennage, et la calibration associée.\

- Une **trace** est une **courbe affichée** à l’écran. Une trace appartient à un canal : elle utilise son balayage, mais elle choisit ce qu’elle montre (quel paramètre, sous quel format).
- Un **paramètre** (ex. S11) est **la grandeur mesurée**.&#32;

Un paramètre S compare une onde qui sort d’un port à une onde qui entre dans un port :

S(i,j) = onde sortant du port i / onde entrant dans le port j

Le premier indice est le port où l’on **mesure**, le second est le port où l’on **envoie le signal**.

### 3.3 Paramètres et formats d’affichage

Paramètres affichés : S11, S21, S12, S22, pour ce faire il faut sélectionner le bouton **MEAS**** **dans l'onglet** ****T****r****a****c****e**** **puis sélectionner le paramètre** ****S**** **voulue.\
\
 Si on veut voir plusieurs paramètre a l’écran (ex S11 et S22) il faut allez dans l'onglet **Trace **puis **T****race ****config**** **et sélectionner** ****A****d****d**** ****T****r****a****c****e**** ****+**** d****i****a****g****r****am**** **

| Format d’affichage | Capture d'écran | Chemin dans le menu |
| --- | --- | --- |
| Magnitude (dB) | dB mag.png | **T****r****ace**** ****-****-****-****>**** ****Format ---> dB Mag** |
| Phase |  Phase et Unwr .png  | **Trace ---> ****Format ---> ****P****ha****s****e** |
| Phase déroulée |  | **Trace --->**** ****Format ****--->** **U****n****w****r**** ****P****h****a****s****e** |
| Diagramme de Smith | \
SWR et Smith.png  | **Trace --->**** ****Format ---> ****S****m****i****t****h** |
| ROS (SWR) |  | **Trace --->**** ****Format ---> ****S****W****R** |
| Affichage polaire |  Polar & Delay.png  | **Trace --->**** ****Format ---> ****P****o****l****a****r** |
| Retard de groupe |  | **Trace --->**** ****Format ---> ****D****e****lay** |

### 3.4 Marqueurs\


Paramètres affichés : j'ai afficher un S11 en format dB mag et j'ai placer plusieurs marqueur, le premier se trouve a la fréquence 16 GHz, le second est un marqueur delta à 10 GHz, le troisième est un marqueur qui affiche le maximum et le dernier et un marqueur minimum&#32;

| Action | Résultat | Chemin dans le menu | Capture d'écran |
| --- | --- | --- | --- |
| Marqueur placé à f = 16 GHz | Valeur :  - 17.7 dB | **Trace ---> ****M****a****r****k****eur****s****---> ****M****k****r1** | Mark1.png |
| Marqueur delta (référence : 16 GHz) | Δf = -6 GHz ; Δ dB = -3.4 dB | **Trace ---> Markeurs---> Mkr1**** ****---> ****D****e****lta**** ****m****o****d****e ****ON** | MarkDelta.png |
| Recherche du maximum | f = 15 GHz ; valeur =  -15.9 dB | **Trace ---> Markeurs---> Mkr**** ****s****e****a****r****c****h**** ****---> ****M****a****x** | MarkMax.png |
| Recherche du minimum | f = 19.4 GHz ; valeur = -33 dB | **Trace ---> Markeurs---> Mkr search ---> M****i****n** | Markmin.png |

---

## 4. Contrôle fonctionnel sans calibration

> Les mesures de cette partie ne sont **pas calibrées** : elles servent à détecter une anomalie évidente, pas à mesurer précisément.

### Configuration utilisée (métadonnées)

| Paramètre | Valeur |
| --- | --- |
| Bande de fréquence | 2 GHz à  18 GHz |
| Nombre de points | 8001 |
| IFBW | 1 kHz |
| Puissance | 0 dBm |
| Moyennage | facteur de 10 |
| Câbles de test (réf., longueur) | Cable Test, 50 cm |
| Adaptateurs | 2 Thru |

### 4.1 Test T1 – Transmission

**Objectif :** vérifier que la chaîne de transmission entre les deux ports fonctionne.

**Montage :** `Port 1 ───`` ``thru ─── câble de test ───`` ``thru ───`` ``Port 2`

| Observation attendue | Observation |
| --- | --- |
| Transmission présente sur toute la bande | on observe aucune anomalie sur tout la bande de fréquence demandé. les -20 dB observé sont du a la nom calibration de l'appareil il ne faut pas les prendre en compte |
| Réponse régulière (pas de creux anormal) | la réponse et bien réguliere , un peu descendante de l'ordre de 1.2 dB sur tout la plage de fréquence |
| Cohérence entre S21 et S12 | Écart : 0.05 dB, ce qui est acceptable |

**Capture d’écran / fichier :**  TEST T1.png, photo test T1

**Conclusion T1 :** Suite a ce test je peu valider le VNA en transmission de signal

### 4.2 Test T2 – Charge 50 Ω

**Objectif :** vérifier la mesure de réflexion.

On reste sur cette configuration mais on observe S11 et S22 en format SWR

| Essai | Montage | Paramètre mesuré | Observation |
| --- | --- | --- | --- |
| 1 | Charge directement sur le port | S11&#32; | les résultat sont cohérent avec ce qu'on peu retrouver avec un charge de 50 Ohm |
| 2 | Charge au bout du câble de test | &#32;S22 | La mesure au bout du câble est un peu dégradé ce qui est normale car elle inclu le cable sachant il ya pas de calibration effectuer |

**Capture d’écran / fichier :**  TEST T2.png, photo test T**2\
\
Conclusion T2 :**  La mesure de réflexion est cohérente avec une charge 50 Ω. Avec la charge directement connectée, le ROS reste inférieur à 1,3 sur toute la bande 2–18 GHz. Les courbes sont régulières, et le ROS augmente légèrement avec la fréquence, comme on l’attend d’une charge réelle.

### 

---

## 5. Bilan de l’activité

| Étape | Résultat | Remarque |
| --- | --- | --- |
| Réception et identification | OK | L'appareil a bien été réceptionné avec tout ces accessoire et il n'a pas d'anomalie détecté&#32;&#32; |
| Première mise sous tension | OK | le démarrage est rapide , il n'affiche pas d'erreur et il valide son self test |
| Prise en main de l’interface | Acquise | les menu / sous menu fonctionne bien aucune anomalie détecté a ce niveau&#32; |
| T1 – Transmission | OK | la transmission est correct il y a pas d’écart significatif  observé en changeant le sens de la transmission |
| T2 – Charge 50 Ω | OK | la réflexion de VNA est correct |
| T3 – Court-circuit | OK | il détecte bien en format SMITH les cour-circuit |
| T4 – Comparaison des ports | OK | il n'a pas de grand écart entre le port 1 et 2 malgré un charge et un câble différent&#32; |

**Le VNA est-il apte à passer à l’étape de calibration ?**&#32;

Oui le VNA peut passer à l’étape suivante de calibration&#32;
