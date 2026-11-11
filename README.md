# Convertisseur SKP local

Convertit un fichier SketchUp `.skp`, ou un ZIP contenant exactement un `.skp`, en fichier `.glb` pour Blender et d'autres visionneuses 3D.

La conversion s'exécute localement : le modèle n'est pas envoyé à un service en ligne. L'installation des dépendances nécessite une connexion Internet; après cette installation, la conversion peut être utilisée hors ligne.

## Installation

Depuis la racine du dépôt :

```powershell
python -m pip install -r requirements-skp-converter.txt
```

## Utilisation

```powershell
python tools/graphics/skp_to_glb.py "chemin\vers\modele.zip" "exports\modele.glb"
```

Le ZIP doit contenir exactement un fichier `.skp`. Les fichiers `.skb` (sauvegardes SketchUp) sont ignorés.

Pour convertir un `.skp` extrait directement :

```powershell
python tools/graphics/skp_to_glb.py "chemin\vers\modele.skp" "exports\modele.glb"
```

Par défaut, les textures sont intégrées. `--no-textures` réduit la taille du résultat; `--force` remplace le GLB et son fichier compagnon `_metadata.json`, qui contient les calques et la hiérarchie des instances.

## Vérification

```powershell
python -m pytest -q
```

Le parseur [OpenSKP](https://github.com/iamahsanmehmood/openskp) est installé comme dépendance distincte (MIT). Aucun fichier de modèle ou rendu ne doit être ajouté au dépôt.
