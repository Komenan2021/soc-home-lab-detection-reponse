# 🛡️ SOC Home Lab — Détection & réponse aux incidents

> Laboratoire SOC complet : **LimaCharlie (EDR)** + **OpenSearch (SIEM)**, simulation d'attaques cartographiées sur **MITRE ATT&CK** et entraînement sur **ACEResponder**.

![EDR](https://img.shields.io/badge/EDR-LimaCharlie-0b6cff) ![SIEM](https://img.shields.io/badge/SIEM-OpenSearch-005EB8) ![Framework](https://img.shields.io/badge/Framework-MITRE%20ATT%26CK-c00) ![Statut](https://img.shields.io/badge/statut-termin%C3%A9-2FA35F)

**Auteur :** Kouakou François Komenan — Analyste SOC / Technicien Réseau, Abidjan
**Portfolio :** https://thefulkom.tech/portfolio/

---

## 🎯 Objectif

Reproduire, dans un environnement de laboratoire, le travail quotidien d'un analyste SOC :

1. **Collecter** les journaux de plusieurs sources (postes, serveurs, réseau).
2. **Détecter** les comportements malveillants grâce à un EDR et à un SIEM.
3. **Simuler** des attaques réelles, cartographiées sur MITRE ATT&CK.
4. **Investiguer** chaque alerte et **répondre** à l'incident.

## 🏗️ Architecture

```
 ┌──────────────────┐      télémétrie EDR       ┌──────────────────┐
 │  Poste Windows   │ ────────────────────────▶ │   LimaCharlie    │
 │  (cible + agent) │                           │   (EDR, cloud)   │
 └────────┬─────────┘                           └────────┬─────────┘
          │ journaux (événements Windows, Sysmon…)       │ alertes / détections
          ▼                                              ▼
 ┌──────────────────────────────────────────────────────────────────┐
 │                   OpenSearch (SIEM)                              │
 │   ingestion · corrélation · tableaux de bord · recherche         │
 └──────────────────────────────────────────────────────────────────┘
          ▲
          │ attaques simulées
 ┌────────┴─────────┐
 │ Machine attaquant │
 └──────────────────┘
```

> 📸 Remplace ce schéma par ton propre diagramme : `images/01-architecture.png`

## ⚙️ Ce qui a été mis en place

| Composant | Rôle | Réalisation |
|---|---|---|
| **LimaCharlie** | EDR | Déploiement de l'agent sur le poste cible, collecte de la télémétrie (processus, réseau, fichiers), règles de détection |
| **OpenSearch** | SIEM | Ingestion et corrélation des journaux multi-sources, création de tableaux de bord |
| **Machine attaquant** | Simulation | Exécution de scénarios d'attaque contrôlés |
| **MITRE ATT&CK** | Référentiel | Classification de chaque technique observée |
| **ACEResponder** | Entraînement | Labs pratiques d'investigation SOC |

## 🧪 Attaques simulées (MITRE ATT&CK)

| ID | Technique | Ce qui est observé | Détection |
|---|---|---|---|
| **T1059** | Command and Scripting Interpreter | Exécution de commandes PowerShell / cmd | Processus enfant suspect, ligne de commande encodée |
| **T1003** | OS Credential Dumping | Tentative de lecture de la mémoire LSASS | Accès au processus `lsass.exe` |
| **T1071** | Application Layer Protocol | Communication réseau sortante type C2 (HTTP/DNS) | Connexions sortantes inhabituelles |

## 🔎 Déroulement

1. **Préparation du lab** : création des machines virtuelles (cible Windows, attaquant) sur un réseau isolé.
2. **Déploiement de l'EDR** : installation de l'agent LimaCharlie sur la cible et vérification de la remontée de télémétrie.
3. **Mise en place du SIEM** : installation d'OpenSearch, configuration de l'ingestion des journaux.
4. **Tableaux de bord** : vues de suivi des connexions, des processus et des alertes.
5. **Simulation d'attaques** : exécution des techniques T1059, T1003 et T1071.
6. **Investigation** : analyse de chaque alerte, distinction vrai / faux positif, chronologie de l'attaque.
7. **Réponse** : isolement de la machine, recommandations de remédiation.

## 📊 Résultats

<!-- ✏️ À compléter avec tes vrais résultats, par exemple : -->
- Nombre de sources de journaux intégrées : _à compléter_
- Règles de détection créées : _à compléter_
- Attaques détectées sur les 3 simulées : _à compléter_
- Principal enseignement : _à compléter_

## 📸 Captures d'écran

| Fichier à déposer dans `images/` | Contenu |
|---|---|
| `01-architecture.png` | Schéma du lab |
| `02-limacharlie-agent.png` | Agent EDR connecté sur le poste cible |
| `03-opensearch-dashboard.png` | Tableau de bord SIEM |
| `04-detection-t1059.png` | Alerte sur l'exécution de commandes |
| `05-detection-t1003.png` | Alerte sur l'accès à LSASS |
| `06-investigation.png` | Chronologie / investigation d'un incident |

![Architecture](images/01-architecture.png)
![Agent LimaCharlie](images/02-limacharlie-agent.png)
![Tableau de bord OpenSearch](images/03-opensearch-dashboard.png)
![Détection T1059](images/04-detection-t1059.png)
![Détection T1003](images/05-detection-t1003.png)
![Investigation](images/06-investigation.png)

## 🧠 Compétences démontrées

`Surveillance SOC` · `EDR` · `SIEM` · `Corrélation de journaux` · `MITRE ATT&CK` · `Investigation d'alertes` · `Réponse aux incidents` · `Gestion des faux positifs`

---

⚠️ *Toutes les attaques ont été réalisées dans un laboratoire isolé, sur des machines m'appartenant, à des fins d'apprentissage.*
