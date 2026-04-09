# 📝 Réglages des Zones LD2450 - Salon
Dernière mise à jour : 9 avril 2026

Voici les réglages optimaux relevés après configuration visuelle. Ces valeurs sont sauvegardées dans la mémoire flash de l'ESP, mais ce fichier sert de référence en cas de réinitialisation complète.

## 🌍 Paramètres Globaux
| Paramètre | Valeur |
| :--- | :--- |
| **Angle du Radar** | 0.0 ° |
| **Any Presence Timeout** | 0.0 s |

---

## 🟩 Zone 1
| Paramètre | Valeur |
| :--- | :--- |
| **Centre X** | 1190 mm |
| **Départ Y** | -500 mm |
| **Largeur** | 2340 mm |
| **Profondeur (Height)** | 2630 mm |
| **Timeout Zone** | 5.0 s |

---

## 🟧 Zone 2
| Paramètre | Valeur |
| :--- | :--- |
| **Centre X** | -790 mm |
| **Départ Y** | 1950 mm |
| **Largeur** | 2410 mm |
| **Profondeur (Height)** | 3820 mm |
| **Timeout Zone** | 5.0 s |

---

## 🟦 Zone 3 (À compléter)
*Pas de réglage relevé pour l'instant.*

---

## 🟥 Zone Exclusion 1 (À compléter)
*Pas de réglage relevé pour l'instant.*

---

> [!TIP]
> Si vous souhaitez que ces valeurs deviennent les valeurs par défaut après un flash "propre" (erase memory), vous pouvez les reporter dans les champs `initial_value` du fichier `.ld2450.yaml`.
