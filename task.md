# 📋 TASK.MD - Panneau de Contrôle Radars LD24xx

## 🏗️ Phase 1 : Infrastructure Cible (Nouveau Dossier)
- [x] Valider le nom officiel : `ha-ld24xx-panneau-de-controle`.
- [x] Créer le nouveau répertoire racine : `/mnt/Data/Github/02-Hardware-Devices/ha-ld24xx-panneau-de-controle`.
- [x] Initialiser `.gitignore` en mode White List dans la cible.
- [x] Créer `PROJET_RULES.md` (Spécificités du dépôt) dans la cible.
- [x] Créer `JOURNAL_MODIFICATIONS.md` et `CONTRIBUER.md` dans la cible.
- [x] Préparer l'arborescence Snapshot par matériel dans la cible.
- [x] Produire l'audit Sentinel de Phase 1.

## 🔄 Phase 2 : Migration & Normalisation (Snapshot v1.0.0)
### 2.1 : Copie Brute (Sécurisation du transfert)
- [x] Copier les fichiers YAML/H du LD2410 vers leurs dossiers cibles (noms originaux).
- [x] Copier les fichiers YAML/H du LD2450 vers leurs dossiers cibles (noms originaux).
- [x] Copier les Assets (Images/GIF) vers `docs/assets/ld2410` et `docs/assets/ld2450`.

### 2.2 : Renommage Snapshot (Standard T5.2)
- [x] Renommer les packages : `radar_[modèle]_v1.0.0.yaml`.
- [x] Renommer les configs ESPHome : `esp_[nom]_v1.0.0.yaml`.
- [x] Renommer les cartes Dashboard : `carte_[modèle]_v1.0.0.yaml`.

### 2.3 : Initialisation du Laboratoire (Lab)
- [x] Créer les dossiers `lab/` pour chaque matériel (centralisé à la racine).
- [x] Générer les fichiers `_PROD.yaml` par copie des originaux.
- [x] Vérifier l'exclusion Git effective (White List Check).

### 2.4 : Audit Sentinel de Phase 2
- [x] Produire l'audit Sentinel de Phase 2 (Parité, Renommage, Lab).

## 🛠️ Phase 3 : Souveraineté & Standardisation Chirurgicale
### Cycle Itératif par fichier : [PROPOSITION ➡️ VALIDATION ➡️ EXÉCUTION]
- [x] Traiter `radar_ld2410_v1.0.0.yaml` (ID/Labels/Rationale/Synchro Lab).
- [x] Traiter `radar_ld2450_v1.0.0.yaml` (ID/Labels/Rationale/Synchro Lab).
- [x] Traiter `esp_radar_salon_v1.0.0.yaml` (ID/Labels/Rationale/Synchro Lab).
- [x] Traiter `esp_radar_salon02_v1.0.0.yaml` (ID/Labels/Rationale/Synchro Lab).
- [x] Traiter `carte_ld2410_v1.0.0.yaml` (ID/Labels/Rationale/Synchro Lab).
- [x] Traiter `carte_ld2450_v1.0.0.yaml` (ID/Labels/Rationale/Synchro Lab).
- [x] Produire l'audit Sentinel de Phase 3.

## 📄 Phase 4 : Documentation & Clôture
- [/] Mettre à jour le `README.md` principal avec assets locaux.
- [ ] Générer le rapport d'audit final `AUDIT_SENTINEL_FINAL_v1.0.0.md`.
- [ ] JALON : Signalement pour Commit Manuel (Commandant).
