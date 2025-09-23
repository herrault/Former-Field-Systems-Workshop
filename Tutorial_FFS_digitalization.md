# Tutorial QGIS – Former Field System Mapathon 

This tutorial describes the collaborative digitization methodology in QGIS for identifying and mapping different types of former field systems observed on LiDAR DEMs.  
The objective is to build a consistent and usable database from four study areas in th Bas-Rhin district, France.

---

## 1. Material

- ** LiDAR DEM** (one for each group).
- **Empty geopackage** :
  - `lines_create.gpkg` → for headlands (ackerberg, G1 only).
  - `polygons_create.gpkg` → for lynchet, ridge and furrows and stone walls (for all groups)
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
3. Ditilalize  **only within your mesh**.
4. After digitalization, fill the attribution fields (see section 4).

---

## 3. FFS classification

see also the powerpoint for illustrations

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

### Ridge and furrows (polygons)
- **Nature** : parallel ridges.  
- **Couche** : `polygons_create.gpkg`.  
- ** Geometry** : polygon (`Polygon`).  
- **A group of several parallel ridge and furrows = 1 polygon comprising several ridges**.

### Stone walls (polygones)
- **Nature** : Stone walls resulting from stone removal forming small plots.  
- ** Layer** : `polygons_create.gpkg`.  - ** Geometry** : polygon (`Polygon`).  
- **A group of small adjacent plots = 1 polygon comprising several organized stone walls**.



---

## 4. Editing datatables

Each digitized object must have the following fields correctly filled in:
| Champ        | Type     | Description |
|--------------|----------|-------------|
| `id_maille`  | Texte / Entier | Grid id (from the 1000×1000 m grid). |
| `type_forme` | Texte    | **Hedland=1** / **lynchet=2** / **ridge and furrow=3**/ **stone walls=4** |
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
- Check that all your objects have a valid `id_maille`.
- Check that `type_forme` corresponds to the typology.
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
