# 🧠 STRATÉGIE DE RESTRUCTURATION : HA-LD24XX-PANNEAU-DE-CONTROLE

## 🔍 I. Analyse de l'Existant (Étape 0)

Le nouveau dépôt sera créé sous le nom `/mnt/Data/Github/02-Hardware-Devices/ha-ld24xx-panneau-de-controle`. La source originale `/mnt/Data/Github/02-Hardware-Devices/ha-ld24xx-radars` restera intacte comme référence. Nous conserverons la séparation fondamentale par matériel pour préserver le contexte spécifique de chaque carte et faciliter le réglage via l'UI.

### 📋 Inventaire & Mapping (Structure Hybride)
Chaque matériel possédera sa propre arborescence Snapshot interne avec des noms de dossiers francisés.

| Fichier Source | Destination (Snapshot) |
| :--- | :--- |
| **[LD2410]** | |
| `ld2410/input_select.yaml` | `ld2410/packages/1.0/1.0.0/radar_ld2410_v1.0.0.yaml` |
| `ld2410/esp-salon.yaml` | `ld2410/esphome/1.0/1.0.0/esp_radar_salon_v1.0.0.yaml` |
| `ld2410/ld2410_dashboard_card.yaml` | `ld2410/cartes_dashboard/1.0/1.0.0/carte_ld2410_v1.0.0.yaml` |
| **[LD2450]** | |
| `ld2450/input_select.yaml` | `ld2450/packages/1.0/1.0.0/radar_ld2450_v1.0.0.yaml` |
| `ld2450/esp-salon02.yaml` | `ld2450/esphome/1.0/1.0.0/esp_radar_salon02_v1.0.0.yaml` |
| `ld2450/zone.h` | `ld2450/esphome/1.0/1.0.0/radar_zones_v1.0.0.h` |
| `ld2450/radar_dashboard_card.yaml` | `ld2450/cartes_dashboard/1.0/1.0.0/carte_ld2450_v1.0.0.yaml` |

> [!IMPORTANT]
> L'audit du miroir `/mnt/Data/Github/01-Systeme-Core/home-assistant/` est abandonné pour garantir l'étanchéité totale du dépôt Hardware.

## 🛡️ II. Arbitrages Stratégiques (Socratic Gate)

### 1. Structure de l'arborescence (T5.2 Hybride)
**Question** : Doit-on regrouper par Nature à la racine ?
**Décision** : NON. On maintient la racine par matériel (`ld2410/`, `ld2450/`). L'arborescence Snapshot `[Nature]/[X.Y]/[X.Y.Z]/` est appliquée au sein de chaque dossier matériel.

### 2. Francisation et Standardisation (T2)
**Question** : Les IDs dans les fichiers YAML doivent-ils être traduits (ex: `salon` -> `salon`, `input_select` -> `entree_selection`) ?
**Décision** : Les Labels et IDs seront francisés pour respecter la souveraineté (T2), tout en conservant des placeholders `A_CHANGER_*` pour la portabilité.

### 3. Isolation Lab/
**Question** : Comment gérer les fichiers avec IDs réels ?
**Décision** : Tout fichier contenant des informations spécifiques à l'instance de production sera déplacé dans `lab/` avec le suffixe `_PROD.yaml`.

## 🚀 III. Plan d'Action (Jalons)

1. **Phase 1** : Création de l'infrastructure (`.gitignore` White List, `PROJET_RULES.md`).
2. **Phase 2** : Migration via `git mv` vers la structure `[Nature]/1.0/1.0.0/`.
3. **Phase 3** : Standardisation (Syntaxe `action:`, Rationale In-Situ, commentaires massifs).
4. **Phase 4** : Documentation (README, Assets, Rapport d'audit final).

---
**Attente de validation : [MISSION_VALIDEE] ou [ACTION_CONFIRMEE]**
