## Quelle est la répartition en pourcentage des ménages selon le temps nécessaire pour obtenir de l’eau potable ?
---

## CONTEXTE ET MÉTHODOLOGIE

Cette analyse s’inscrit dans l’objectif d’affiner notre maîtrise des outils d’analyses statistiques. 
Pour répondre à cette question, nous avons utilisé la base de données de la **Cinquième Enquête Démographique et de Santé du Bénin de 2017-2018 (EDSB-V 2017-2018)**. La population cible est l’ensemble des ménages enquêtés et donc c’est la base **BJHR71FL** (HR pour Household Recode) qui a été utilisé. Les analyses ont été faites avec le logiciel **SPSS** et les variables utilisées sont présentées dans le tableau ci-dessous.

| Variables | Type | Description | Valeurs/modalités |
| --------- | -----| ------------| ------------------|
| **HV005** | Quantitative | Disponible dans la base HR (Household Recode) , elle contient les poids de chaque ménage,  multipliés par 1000 000 | - |
| **POIDS** | Quantitative | Variable créée à partir de la variable HV005 en divisant ses valeurs par 1000 000. Elle contient donc les véritables poids des ménages | - |
| **HV204** | Qualitative | Disponible dans la base HR (Household Recode). Elle contient le temps nécessaire à chaque ménage pour obtenir de l’eau. Le temps nécessaire pour obtenir de l'eau potable correspond à la somme des minutes nécessaires pour se rendre à la source d'eau, du temps d'attente pour obtenir de l'eau, du temps de collecte de l'eau et du temps de retour de la source d'eau. | - |
| **TWATER** | Qualitative | Variable créée à partir de la variable HV204. | Les classifications relatives au temps d'obtention de l'eau sont les suivantes : eau sur place, moins de 30 minutes et 30 minutes ou plus. |

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

---
## RÉSULTATS
![Temps pour s'aprovisionner en eau](<Temps pour s'aprovisionner en eau.png>)

De nos analyses, il ressort que :
- environ **71%** de la population utilise une source d’eau Améliorée (canalisé dans l'habitation, raccordement par canalisation à la cour/au terrain, raccordement par canalisation au voisin, robinet public/borne-fontaine, puits tubulaire ou forage, puits protégé, source protégée, eau de pluie) ;
- environ **28%** utilisant une source non Améliorée. Ce pourcentage varie en fonction du milieu de résidence (urbain ou rurale).

---
## VÉRIFICATION DES RÉSULTATS
Que dit le rapport de l'EDS-V 2017-2018 ?

- [x] Les résultats de l’**EDSB-V 2017-2018** montrent 
qu’environ sept ménages sur dix **71%** consomment 
de l’eau provenant d’une source améliorée.
- [x] À l’opposé, les ménages dont l’eau de consommation ne 
provient pas d’une source améliorée représentent 
**28%**.

---
## DOCUMENTS UTILISÉS
- **Guide to DHS Statistics DHS-7** pour formuler notre question d'analyse et pour le recodage des variables plus précisément la **section 2.1 (*Household Drinking Water*) du chapitre 2 (*Population and Housing*)** 
- **Rapport de la Cinquième Enquête Démographique et de Santé du Bénin de 2017-2018 (EDSB-V 2017-2018)** pour la vérification de nos résultats. Plus précisément la **section 2.1 (*SOURCES D’APPROVISIONNEMENT EN EAU DE BOISSON ET 
TRAITEMENT*) du chapitre 2 (*CARACTÉRISTIQUES DES LOGEMENTS ET DE LA POPULATION DES MÉNAGES*)** .