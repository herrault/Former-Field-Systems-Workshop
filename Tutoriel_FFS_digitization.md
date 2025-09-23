# Tutoriel QGIS – Mapathon Formes agraires

Ce tutoriel décrit la méthodologie de numérisation collaborative dans QGIS pour identifier et cartographier différents types de formes agraires observées sur des MNT LiDAR.  
L’objectif est de constituer une base de données homogène et exploitable à partir de plusieurs zones d’étude.

---

## 1. Données de travail

- **MNT LiDAR** (4 zones disponibles).
- **Jeux de données vides** (GeoPackage) :
  - `lines_create.gpkg` → pour les *ackerberg* (formes linéaires).
  - `polygons_create.gpkg` → pour les *rideaux de culture* et *champs bombés* (formes surfaciques).
- **Maillage 1000 m x 1000 m** → pour découper l’avancement du travail.  
  Chaque maille possède un identifiant unique (champ `id_maille`).

⚠️ Tous les fichiers sont déjà dans le **bon système de coordonnées**.

---

## 2. Organisation du mapathon

1. Chaque binome choisit une maille (1000 m × 1000 m) de son groupe. Commencer en haut à gauche. Chaque binome se réserve 2 lignes. Le binome 1 commence à la ligne 1, le binome 2 à la ligne 3, le binome 3 à la ligne 5 etc
2. Le binome ouvre :
   - le MNT correspondant,
   - le maillage,
   - le GeoPackage (`lines_create.gpkg` ou `polygons_create.gpkg`) en édition.
3. Il numérise **uniquement dans sa maille**.
4. Après numérisation, il renseigne correctement les champs attributaires (voir section 4).

---

## 3. Typologie des formes agraires

### Ackerberg (lignes)
- **Nature** : structures linéaires visibles dans le MNT.  
- **Couche** : `lines_create.gpkg`.  
- **Géométrie** : ligne (`LineString`).  
- **Un objet = une ligne**.

### Rideaux de culture (polygones)
- **Nature** : parcellaire de plusieurs rideaux de culture.  
- **Couche** : `polygons_create.gpkg`.  
- **Géométrie** : polygone (`Polygon`).  
- **Un objet = un polygone regroupant plusieurs rideaux**.

### Champs bombés (polygones)
- **Nature** : relief bombé d’une parcelle.  
- **Couche** : `polygons_create.gpkg`.  
- **Géométrie** : polygone (`Polygon`).  
- **Un objet = un ensemble de parcelles bombés parallèles**.

### Murger (polygones)
- **Nature** : relief bombé d’une parcelle.  
- **Couche** : `polygons_create.gpkg`.  
- **Géométrie** : polygone (`Polygon`).  
- **Un objet = un parcellaire de murgers **.



---

## 4. Edition des tables attributaires

Chaque objet numérisé doit avoir les champs suivants correctement renseignés :

| Champ        | Type     | Description |
|--------------|----------|-------------|
| `id_maille`  | Texte / Entier | Identifiant de la maille (repris du maillage 1000×1000 m). |
| `type_forme` | Texte    | **ackerberg** / **rideau** / **champ**/ **murger** |
| `commentaire`| Texte libre | (optionnel) Observations particulières, incertitudes. |

💡 **Astuce** : utiliser l’outil de capture dans QGIS pour remplir automatiquement `id_maille` en cliquant sur la maille correspondante.

---

## 5. Bonnes pratiques de numérisation

- Toujours activer **l’accrochage** (snapping) pour assurer des limites précises.  
- Sauvegarder régulièrement ses modifications (icône disquette).  
- Vérifier après chaque session que les champs attributaires sont correctement remplis.
- Ne pas déborder de la maille. Pour un objet à cheval on suit la limite de la maille (polygones) et on laisse le bout de l'objet pour le binome responsable de l'autre maille

---

## 6. Étapes pratiques dans QGIS

1. **Charger les données**
   - Ouvrir le projet QGIS.
   - Ajouter le MNT (Raster LiDAR).
   - Ajouter le maillage (vecteur).
   - Ajouter les couches de création (`lines_create.gpkg` et `polygons_create.gpkg`).

2. **Activer l’édition**
   - Clic droit sur la couche → *Basculer en mode édition*.
   - Sélectionner l’outil *Numériser une nouvelle entité*.

3. **Numériser la forme**
   - Tracer l’objet à l’écran.
   - Valider l’objet.
   - Remplir les champs dans la fenêtre attributaire (cf. section 4).

4. **Enregistrer**
   - Cliquer sur l’icône *Enregistrer les modifications*.
   - Ne pas oublier de quitter le mode édition à la fin de la session.

---

## 7. Contrôle qualité

Avant de soumettre votre travail :
- Vérifiez que tous vos objets ont un `id_maille` valide.  
- Vérifiez que `type_forme` correspond bien à la typologie.  
- Supprimez les entités test/incomplètes.  
- Contrôlez que les objets ne sortent pas de la maille choisie.

---

## 8. Dépôt collaboratif

- Une fois la session terminée, exportez vos couches mises à jour.  
- Partagez-les selon l’organisation définie (voir avec le coordinateur de votre groupe).  
- Utilisez un nom clair pour vos fichiers (exemple : `lines_Name_Groupnumber.gpkg, polygons_Name_Groupnumber.gpkg).

---

✍️ **Merci pour votre participation !**  
- Chaque contribution compte pour documenter et valoriser le patrimoine agraire 
- N'oubliez pas de recuperer votre sandwich et votre ticket valable pour une boisson à la Kfet

# Tutorial QGIS – Former Field System Mapathon 

This tutorial describes the collaborative digitization methodology in QGIS for identifying and mapping different types of former field systems observed on LiDAR DEMs.  
The objective is to build a consistent and usable database from four study areas in th Bas-Rhin district, France.

---

## 1. Material

- ** LiDAR DEM** (one for each group).
- **Empty geopackage** :
  - `lines_create.gpkg` → for headlands (ackerberg, G1 only).
  - `polygons_create.gpkg` → for lynchet, ridge and furrows and stone walls
- **Grid 1000 m x 1000 m** → to organize the progression into each group.  
  Each mesh has a unique identifier. (champ `id_maille`).

⚠️ All files are already in the **correct coordinate system**.
---

## 2. Methodology

1. Each pair of participants chooses a grid square (1000 m × 1000 m) from their group. Start at the top left. Each pair reserves two lines. Pair 1 starts at line 1, pair 2 at line 3, pair 3 at line 5, and so on.2. 
The pair open:
   - the DEM of his group,
   - the grid,
   - the GeoPackage (`lines_create.gpkg` ou `polygons_create.gpkg`) in edition mode.
3. Scan  **only within your mesh**.
4. After digitalization, fill the attribution fields (see section 4).

---

## 3. FFS classification

### Headlands / Ackerberg (lines)
- **Nature** : linear structures visible in the DEM.  
- **Layer** : `lines_create.gpkg`.  
- **Geometry** : line (`LineString`).  
- **1 headland = 1 line**.

### Lynchet (polygons)
- **Nature** : parceling of several lynchets.  
- **Layer** : `polygons_create.gpkg`.  
- **Geometry** : polygon (`Polygon`).  
- **1 area covered by lynchet = 1 polygon comprising several lynchets**.

### Ridges and furrows (polygons)
- **Nature** : parallel ridges.  
- **Couche** : `polygons_create.gpkg`.  
- ** Geometry** : polygon (`Polygon`).  
- **A group of several parallel ridge and furrows= 1 polygon comprising several ridges**.

### Stone walls (polygones)
- **Nature** : Stone walls resulting from stone removal forming small plots.  
- ** Layer** : `polygons_create.gpkg`.  - ** Geometry** : polygon (`Polygon`).  
- **A group of small adjacent plots = 1 polygon comprisinf several organized stone walls**.



---

## 4. Editing datatables

Each digitized object must have the following fields correctly filled in:
| Champ        | Type     | Description |
|--------------|----------|-------------|
| `id_maille`  | Texte / Entier | Grid id (from the 1000×1000 m grid). |
| `type_forme` | Texte    | **Hedland** / **lynchet** / **ridge and furrow**/ **stone walls** |
| `remark`| Free text | (optionnal) Obervations and uncertainties. |

💡 **Tip**: Use the capture tool in QGIS to automatically fill in `id_cell` by clicking on the corresponding cell.

---

## 5. Best practices for digitization

- Always enable snapping to ensure precise boundaries.
- Save your changes regularly (floppy disk icon).
- After each session, check that the attribute fields are filled in correctly.
- Do not go beyond the mesh. For an object that straddles two meshes, follow the mesh boundary (polygons) and leave the end of the object for the pair responsible for the other mesh.
---

## 6. Practical steps in QGIS

1. **Load the data**
   - Open the QGIS project.
   - Add the DEM (LiDAR raster).
   - Add the mesh (vector).
   - Add the creation layers. (`lines_create.gpkg` et `polygons_create.gpkg`).

2. ****Enable editing**
   - Right-click on the layer → *Switch to edit mode*.
   - Select the * tool.*Numériser une nouvelle entité*.

3. **Digitize the shape**
   - Trace the object on the screen.
   - Validate the object.
   - Fill in the fields in the attribute table (see section 4).
4. **Save**
   - Click on the *Save changes* icon.
   - Don't forget to exit edit mode at the end of the session.
---

## 7. Quality control

Before submitting your work:
- Check that all your objects have a valid `id_mesh`.
- Check that `type_shape` corresponds to the typology.
- Delete test/incomplete entities.
- Check that the objects do not extend beyond the selected mesh.
---

## 8. Collaborative repository

- Once the session is over, export your updated layers.
- Share them according to the defined organization (check with your group coordinator).
- Use a clear name for your files (example: `lines_Name_Groupnumber.gpkg, polygons_Name_Groupnumber.gpkg).
---

✍️ **Thank you for participating! **  
- Every contribution counts toward documenting and promoting agricultural heritage. 
- Don't forget to pick up your sandwich and your ticket for a drink at the Kfet.

