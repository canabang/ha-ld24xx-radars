# 📡 HA-LD24xx-Radars

Bienvenue dans la collection de configurations haute performance pour les modules radars de présence temporelle (mmWave 24GHz) **HiLink HLK-LD2410** et **HLK-LD2450** dans **Home Assistant**.

Ce dépôt regroupe de manière centralisée les firmwares **ESPHome** avancés ainsi que des **Dashboards dynamiques et unifiés** interactifs (rendu graphique via Plotly).

## 💡 Le Projet
Les radars mmWave sont aujourd'hui la référence pour la détection de présence statique (respiration, micro-mouvements) dans les scénarios domotiques (ex: maintenir la lumière allumée tant que quelqu'un est assis sur le canapé).

### 🆚 LD2410 vs LD2450 : Lequel choisir ?
* **LD2410** : Idéal pour les petites à moyennes pièces fermées (salles de bain, toilettes, bureaux). Détecte par couches de distances radiales (les "Gates"). Fonctionne en 1D (Distance pure).
* **LD2450** : Mieux adapté aux grands espaces ouverts (salon, cuisine). Suivi multi-cibles simultanées (jusqu'à 3 personnes) et notion de "Zones de couverture 2D" complètes (Axe X/Y).

## 🙏 Crédits
* **LD2450** : Basé sur le projet [53l3cu5/ESP32_LD2450](https://github.com/53l3cu5/ESP32_LD2450) (⚠️ **plus maintenu**). Outil de génération : [53l3cu5.github.io](https://53l3cu5.github.io).
* **LD2410** : Utilise le composant natif `ld2410` d'ESPHome.

## 🏷️ Convention de Nommage (IMPORTANT)
Les Dashboards dynamiques construisent les noms d'entités **par concaténation** du nom de l'ESP sélectionné dans la liste déroulante.

> **⚠️ Le nom dans `input_select` DOIT correspondre EXACTEMENT au `name:` de l'appareil ESPHome.**

## 📦 Dépendances UI Requises (Home Assistant)
1. `Mushroom Cards`
2. `Plotly Graph Card`
3. `Config Template Card`
4. `Tabbed Card`
5. `Stack In Card`

## 🔧 Installation Rapide (Architecture Modulaire)
### 1. ESPHome
```yaml
packages:
  ld2410: !include .ld2410.yaml
```

### 2. Home Assistant - Input Select
Ajoutez le bloc `liste_esp_ld24xx` dans votre fichier `input_select.yaml`.

### 3. Dashboard
Copiez/collez le contenu du fichier `*_dashboard_card.yaml` dans une nouvelle carte manuelle.

## ⚡ Substitutions : Mode Réglage vs Mode Production
| Mode             | Utilité | Valeurs LD2410 | Valeurs LD2450 |
| ---------------- | ------- | -------------- | -------------- |
| **🔧 Réglage**    | Calibration | `1s` | `250ms` |
| **🏠 Production** | Usage stable | `60s` / `15s` | `1500ms` |
