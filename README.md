# 📡 HA-LD24xx-Radars

Bienvenue dans la collection de configurations haute performance pour les modules radars de présence temporelle (mmWave 24GHz) **HiLink HLK-LD2410** et **HLK-LD2450** dans **Home Assistant**.

Ce dépôt regroupe de manière centralisée les firmwares **ESPHome** avancés ainsi que des **Dashboards dynamiques et unifiés** interactifs (rendu graphique via Plotly).

## 💡 Le Projet
Les radars mmWave sont aujourd'hui la référence pour la détection de présence statique (respiration, micro-mouvements) dans les scénarios domotiques (ex: maintenir la lumière allumée tant que quelqu'un est assis sur le canapé).

### 🆚 LD2410 vs LD2450 : Lequel choisir ?
* **LD2410** : Idéal pour les petites à moyennes pièces fermées (salles de bain, toilettes, bureaux). Détecte par couches de distances radiales (les "Gates"). Fonctionne en 1D (Distance pure).
* **LD2450** : Mieux adapté aux grands espaces ouverts (salon, cuisine). Suivi multi-cibles simultanées (jusqu'à 3 personnes) et notion de "Zones de couverture 2D" complètes (Axe X/Y).

## 🚀 Architecture du Dépôt
Le dépôt se compose de deux parties majeures :

### 📂 `/ld2410` (Détection par Gates)
- Firmware optimisé avec gestion fine du bruit (`throttle` et `delta` sur les vagues d'énergie).
- Dashboard Plotly affichant en temps réel les énergies cinétiques "Move" et "Still" face aux seuils.
- Calcul visuel interactif : Les sliders de portes basculent automatiquement en mètres selon la "Résolution de distance" (ex: G1 affiche directement "0.75m").

### 📂 `/ld2450` (Cartographie 2D)
- Firmware réécrit pour exposer l'ensemble des réglages et capteurs **en mètres**.
- Visualisation temps réel des cibles (jusqu'à 3) sur plan 2D.
- Gestion logicielle de **l'angle d'inclinaison** du capteur.
- Option **"Target Must Leave Zone"** par zone pour verrouiller la présence et supprimer le flickering d'éclairage.

## 🙏 Crédits
* **LD2450** : Basé sur le projet [53l3cu5/ESP32_LD2450](https://github.com/53l3cu5/ESP32_LD2450) (⚠️ **plus maintenu**). Outil de génération : [53l3cu5.github.io](https://53l3cu5.github.io).
* **LD2410** : Utilise le composant natif `ld2410` d'ESPHome.

## 🏷️ Convention de Nommage (IMPORTANT)
Les Dashboards dynamiques construisent les noms d'entités **par concaténation** du nom de l'ESP sélectionné dans la liste déroulante.

Exemple avec `esp_salon02` sélectionné :
```
sensor.esp_salon02_radar_target1_x
number.esp_salon02_radar_zone1_x
binary_sensor.esp_salon02_radar_zone1_presence
```

> **⚠️ Le nom dans `input_select` DOIT correspondre EXACTEMENT au `name:` de l'appareil ESPHome.** Pas de majuscules, pas d'espaces, uniquement `[a-z0-9_]`. Une seule différence = entités "Inconnu".

## 📦 Dépendances UI Requises (Home Assistant)
Pour profiter des Dashboards fournis dans ce dépôt, les modules frontend HACS suivants sont indispensables :
1. `Mushroom Cards` : Pour les contrôleurs et sliders (sliders LD2450 en M).
2. `Plotly Graph Card` : Cœur graphique du système pour générer les radars visuels interactifs dynamiques.
3. `Config Template Card` : Permet l'injection des variables dynamiques en Javascript (le sélecteur multipièces).
4. `Tabbed Card` : Pour l'ergonomie par onglets des réglages des zones.
5. `Stack In Card` : Pour lier tous les composants esthétiquement.

## 🔧 Installation Rapide (Architecture Modulaire)
Ce projet repose sur une architecture **modulaire par `!include`**, tant côté ESPHome que côté Home Assistant.

### 1. ESPHome
Chaque fichier de configuration radar (`.ld2410.yaml`, `.ld2450.yaml`) est conçu pour être **inclus** dans le fichier principal de votre appareil ESP :
```yaml
# Fichier : esp_sdb.yaml (exemple)
packages:
  ld2410: !include .ld2410.yaml
```

### 2. Home Assistant - Input Select
Chaque sous-dossier contient un fichier `input_select.yaml` prêt à l'emploi.
Si votre `configuration.yaml` utilise déjà la directive :
```yaml
input_select: !include input_select.yaml
```
Ajoutez simplement le bloc `liste_esp_ld24xx` dans votre fichier `input_select.yaml` existant.

> **⚠️ Si le fichier `input_select.yaml` n'existe pas encore**, créez-le à la racine de votre configuration Home Assistant et ajoutez la directive `input_select: !include input_select.yaml` dans votre `configuration.yaml`.

### 3. Dashboard
Copiez/collez le contenu du fichier `*_dashboard_card.yaml` dans une nouvelle carte en mode "Éditeur de code manuel".

## ⚡ Substitutions : Mode Réglage vs Mode Production
Chaque fichier ESPHome utilise des **substitutions** pour contrôler la fréquence de remontée des données.

| Mode | Utilité | Valeurs LD2410 | Valeurs LD2450 |
|---|---|---|---|
| **🔧 Réglage** | Dashboard réactif pour calibrer les zones et seuils | `gate_throttle: 1s` / `energy_throttle: 1s` | `uart_throttle_ms: "250"` |
| **🏠 Production** | Usage quotidien (économise Wi-Fi, CPU et base de données) | `gate_throttle: 60s` / `energy_throttle: 15s` | `uart_throttle_ms: "1500"` |

> **Par défaut, les fichiers sont livrés en mode Production.** Pour passer en mode Réglage, modifiez simplement les valeurs dans la section `substitutions:` du fichier `.ld24xx.yaml`, reflashez le capteur, puis restaurez les valeurs de Production une fois la calibration terminée.
