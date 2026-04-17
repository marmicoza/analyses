## Quelle est la répartition en pourcentage des ménages selon le temps nécessaire pour obtenir de l’eau potable ?
---

## CONTEXTE ET MÉTHODOLOGIE

Cette analyse s’inscrit dans l’objectif d’affiner notre maîtrise des outils d’analyses statistiques. 
Pour répondre à cette question, nous avons utilisé la base de données de la **Cinquième Enquête Démographique et de Santé du Bénin de 2017-2018 (EDSB-V 2017-2018)**. La population cible est l’ensemble des ménages enquêtés et donc c’est la base **BJHR71FL** (HR pour Household Recode) qui a été utilisé. Les analyses ont été faites avec le logiciel **SPSS** et les variables utilisées sont présentées dans le tableau ci-dessous.

| Variables | Type | Description | Valeurs/modalités |
| --------- | -----| ------------| ------------------|
| **HV005** | Quantitative | Disponible dans la base HR (Household Recode) , elle contient les poids de chaque ménage,  multipliés par 1000 000 | - |
| **POIDS** | Quantitative | Variable créée à partir de la variable V005 en divisant ses valeurs par 1000 000. Elle contient donc les véritables poids des ménages | - |
| **HV201** | Qualitative | Disponible dans la base HR (Household Recode) Elle contient les différentes sources d’eau potable. | Canalisé dans l'habitation, Raccordement par canalisation à la cour/au terrain, Raccordement par canalisation au voisin, Robinet public/borne-fontaine, Puits tubulaire ou forage, Puits protégé, Puits non protégé, Source protégée, Source non protégée, Rivière/barrage/lac/étang/ruisseau/canal/canal d'irrigation, Eau de pluie, Camion-citerne, Chargeuse avec petite citerne, Eau en bouteille, Sachets d'eau, Autre |
| **SWATER** | Qualitative | Variable créée à partir de la variable HV201 contenant la catégorisation des sources d’eau potable en sources améliorées ou non améliorées | **Sources Améliorées :** Canalisé dans l'habitation, Raccordement par canalisation à la cour/au terrain, Raccordement par canalisation au voisin, Robinet public/borne-fontaine, Puits tubulaire ou forage, Puits protégé, Source protégée, Eau de pluie. **Sources non Améliorées :** Source non protégée, Puits non protégé, Rivière/barrage/lac/étang/ruisseau/canal/canal d'irrigation, Camion-citerne, Chargeuse avec petite citerne, Eau en bouteille, Sachets d'eau |

Nous avons observé **27 valeurs manquantes sur 14 156 observation soit 0.2%**, ce qui est donc négligeable. Nous avons donc écarté les valeurs manquantes avant de poursuivre notre analyse. Nous avons analysé au total **14 129 observations**.

**COMMANDES SPSS**
```spss
* Pondération de la base.
COMPUTE POIDS = HV005 / 1000000.
WEIGHT BY POIDS.

* Temps d'approvisionnement en eau au sein de la population.
FREQ HV204.

* Temps d'approvisionnement en eau au sein de la population d'après le guide DHS.
RECODE HV204 (996 = 1) (0 thru 29 = 2) (30 thru 610 = 3) (998 = 4) INTO TWATER.
VARIABLE LABELS TWATER "Temps pour s'approvisionner en eau".
VALUE LABELS TWATER 1"Eau sur place"
2"Moins de 30 minutes"
3"30 minutes ou plus"
4"Ne sait pas".
FREQ TWATER.

GRAPH
  /BAR(SIMPLE)=COUNT BY TWATER.
```