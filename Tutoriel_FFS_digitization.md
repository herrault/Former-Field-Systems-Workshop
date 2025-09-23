# Tutoriel QGIS – Mapathon Formes agraires

Ce tutoriel décrit la méthodologie de numérisation collaborative dans QGIS pour identifier et cartographier différents types de formes agraires observées sur des MNT LiDAR.  
L’objectif est de constituer une base de données homogène et exploitable à partir de plusieurs zones d’étude.

---

## 1. Données de travail

- **MNT LiDAR** (4 zones disponibles).
- **Jeux de données vides** (GeoPackage) :
  - `lines_create.gpkg` → pour les *ackerberg* (formes linéaires).
  - `polygons_create.gpkg` → pour les *rideaux de culture* et *champs bombés* (formes surfaciques).
- **Maillage 500 m x 500 m** → pour découper l’avancement du travail.  
  Chaque maille possède un identifiant unique (champ `id_maille`).

⚠️ Tous les fichiers sont déjà dans le **bon système de coordonnées**.

---

## 2. Organisation du mapathon

1. Chaque participant choisit une maille (500 × 500 m).
2. Le participant ouvre :
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
- **Un objet = une parcelle bombée**.

---

## 4. Edition des tables attributaires

Chaque objet numérisé doit avoir les champs suivants correctement renseignés :

| Champ        | Type     | Description |
|--------------|----------|-------------|
| `id_maille`  | Texte / Entier | Identifiant de la maille (repris du maillage 500×500 m). |
| `type_forme` | Texte    | **ackerberg** / **rideau** / **champ** |
| `commentaire`| Texte libre | (optionnel) Observations particulières, incertitudes. |

💡 **Astuce** : utiliser l’outil de capture dans QGIS pour remplir automatiquement `id_maille` en cliquant sur la maille correspondante.

---

## 5. Bonnes pratiques de numérisation

- Toujours activer **l’accrochage** (snapping) pour assurer des limites précises.  
- Sauvegarder régulièrement ses modifications (icône disquette).  
- Vérifier après chaque session que les champs attributaires sont correctement remplis.  

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
- Partagez-les selon l’organisation définie (dépôt GitHub, cloud partagé, etc.).  
- Utilisez un nom clair pour vos fichiers (exemple : `lines_VotreNom.gpkg`, `polygons_VotreNom.gpkg`).

---

✍️ **Merci pour votre participation !**  
Chaque contribution compte pour documenter et valoriser le patrimoine agraire 
