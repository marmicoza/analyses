# ANALYSE 1
---

## Question spécifique
Quelles catégories de sources d'approvisionnement en eau les ménages utilisent-ils au Bénin (sources améliorées, sources non-améliorées, autres)?
---

## MÉTHODOLOGIE
- ***Population d'étude:*** Les ménages interviewers lors de l’Enquête Démographique et de Santé 2017-2018 (Rapport EDS 2017-2018, p. 10) soit la base BJHR71FL
- ***Logiciel utilisé:*** SPSS
- ***Variable utilisées:***

| Variables | Type | Description | Valeurs/modalités |
| --------- | -----| ------------| ------------------|
| HV005 | Quantitative | Disponible dans la base HR (Household Recode) , elle contient les poids de chaque ménage,  multipliés par 1000 000 | - |
| POIDS | Quantitative | Variable créée à partir de la variable V005 en divisant ses valeurs par 1000 000. Elle contient donc les véritables poids des ménages | - |
| HV201 | Qualitative | Disponible dans la base HR (Household Recode) Elle contient les différentes sources d’eau potable. | Canalisé dans l'habitation, Raccordement par canalisation à la cour/au terrain, Raccordement par canalisation au voisin, Robinet public/borne-fontaine, Puits tubulaire ou forage, Puits protégé, Puits non protégé, Source protégée, Source non protégée, Rivière/barrage/lac/étang/ruisseau/canal/canal d'irrigation, Eau de pluie, Camion-citerne, Chargeuse avec petite citerne, Eau en bouteille, Sachets d'eau, Autre |
| SWATER | Qualitative | Variable créée à partir de la variable HV201 contenant la catégorisation des sources d’eau potable en sources améliorées ou non améliorées | **Sources Améliorées :** Canalisé dans l'habitation, Raccordement par canalisation à la cour/au terrain, Raccordement par canalisation au voisin, Robinet public/borne-fontaine, Puits tubulaire ou forage, Puits protégé, Source protégée, Eau de pluie. **Sources non Améliorées :** Source non protégée, Puits non protégé, Rivière/barrage/lac/étang/ruisseau/canal/canal d'irrigation, Camion-citerne, Chargeuse avec petite citerne, Eau en bouteille, Sachets d'eau |

- ***Valeurs manquantes :*** 27 sur 14 156 soit 0.2%, ce qui est donc négligeable. Nous avons donc écarté les valeurs manquantes avant de poursuivre notre analyse. Cette suppression n’entraîne pas de perte d’informations significative. Nous avons analysé au total 14 129 observations.

---
## COMMANDES 
### COMMANDES SPSS
```spss
* Pondération de la base.
COMPUTE POIDS=V005/1000000.
WEIGHT BY POIDS.

* Répartition des sources d'eau.
FREQ HV201.

* Création des catégories de sources d'eau: source améliorées, non améliorées et autres.
RECODE HV201 (11 thru 14=1) (21=1) (31=1) (41=1) (51=1) 
    (32=2) (42=2) (43=2) (61 thru 62=2)
     (96=3)   
    INTO SWATER.
VARIABLE LABELS  SWATER "Sources d'eau".
VALUE LABELS SWATER 1"Ameliorees" 
2"Non ameliorees" 
3"Autres".

*Répartition des catégories de sources d'eau.
FREQ SWATER.
```

### COMMANDES R
```r

```
---
## RÉSULTATS
Quelles catégories de sources d'approvisionnement en eau les ménages utilisent-ils (sources améliorées, sources non-améliorées, autres) ?
<img width="2165" height="2500" alt="Répartition des catégories de sources d&#39;eau" src="https://github.com/user-attachments/assets/45274565-95f1-414c-89f4-6abe76b8d08b" />
**Source :** Réalisé à partir des données de l'EDS sous Excel

De nos analyses, il ressort que :
- environ **71%** de la population utilise une source d’eau Améliorée (canalisé dans l'habitation, raccordement par canalisation à la cour/au terrain, raccordement par canalisation au voisin, robinet public/borne-fontaine, puits tubulaire ou forage, puits protégé, source protégée, eau de pluie) ;
- environ **28%** utilisant une source non Améliorée. Ce pourcentage varie en fonction du milieu de résidence (urbain ou rurale).

---
## VÉRIFICATION DES RÉSULTATS
Que dit le rapport de l'EDS-V 2017-2018 ?

- [x] Les résultats de l’EDSB-V 2017-2018 montrent 
qu’environ sept ménages sur dix **71%** consomment 
de l’eau provenant d’une source améliorée.
- [x] À l’opposé, les ménages dont l’eau de consommation ne 
provient pas d’une source améliorée représentent 
**28%**.


