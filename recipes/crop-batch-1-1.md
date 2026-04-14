---
title: "Crop batch 1:1 au centre"
date: 2026-04-14
tags: [crop, batch]
---

# Crop batch 1:1 au centre

## Commande
"Crop les PNG de [dossier] en 1:1 au centre. Sauvegarde dans [dossier]/crops/"

## Workflow agent
1. `list_files` → scanner le dossier source (filtrer par extension)
2. `create_directory` → créer le dossier de sortie
3. `crop_image` × N → pour chaque fichier, crop 1:1 anchor center
4. Rapport: "N/N fichiers croppés"

## Notes
- Les fichiers avec accents dans le nom nécessitent encodeURI (voir bugs/osascript-accents.md)
- Le crop garde le côté court au maximum
