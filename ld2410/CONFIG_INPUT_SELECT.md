# ⚙️ Configuration de l'Input Select (Menu Déroulant)

Pour que la carte fonctionne, vous devez ajouter ce bloc dans votre fichier **`input_select.yaml`** (situé à la racine de votre configuration Home Assistant) :

```yaml
liste_esp_ld2410:
  name: "Choisir un radar LD2410"
  icon: mdi:radar
  options:
    - esp_multi_capteur
    - esp_salon
    - esp_sdb
    - esp_chambre
    - esp_cuisine
```

Si vous ajoutez un nouvel ESP à l'avenir, il vous suffira de rajouter son préfixe dans cette liste `options` pour qu'il apparaisse automatiquement dans la carte !
