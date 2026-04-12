# 📝 Réglages des Zones LD2450 - Salon
Dernière mise à jour : 10 avril 2026

Voici les réglages optimaux relevés après configuration visuelle (valeurs en mètres). Ces valeurs correspondent aux `initial_value` du fichier `.ld2450.yaml`.

## 🌍 Paramètres Globaux
| Paramètre | Valeur |
| :--- | :--- |
| **Angle du Radar** | 0.0 ° |
| **Any Presence Timeout** | 0 s |

---

## 🟩 Zone 1
| Paramètre | Valeur (m) |
| :--- | :--- |
| **Centre (X)** | 1.35 m |
| **Départ (Y)** | -0.50 m |
| **Largeur** | 2.25 m |
| **Profondeur (Height)** | 2.30 m |
| **Timeout Zone** | 0 s |

---

## 🟧 Zone 2
| Paramètre | Valeur (m) |
| :--- | :--- |
| **Centre (X)** | -0.85 m |
| **Départ (Y)** | 1.30 m |
| **Largeur** | 2.25 m |
| **Profondeur (Height)** | 2.10 m |
| **Timeout Zone** | 0 s |

---

## 🟦 Zone 3 (Désactivée)
| Paramètre | Valeur (m) |
| :--- | :--- |
| **Centre (X)** | -4.00 m |
| **Départ (Y)** | -0.50 m |
| **Largeur** | 0.00 m |
| **Profondeur (Height)** | 0.00 m |
| **Timeout Zone** | 0 s |

---

## 🟥 Zone Exclusion 1
| Paramètre | Valeur (m) |
| :--- | :--- |
| **Centre (X)** | 4.00 m |
| **Départ (Y)** | 3.15 m |
| **Largeur** | 8.00 m |
| **Profondeur (Height)** | 4.90 m |

---

> [!TIP]
> Si vous souhaitez que ces valeurs deviennent les valeurs par défaut après un flash "propre" (erase memory), vous pouvez les reporter dans les champs `initial_value` du fichier `.ld2450.yaml`.
