# Part 6 – Material Composition: Supplier Model vs. IDTA 02035-6

deletions are **marked** (`#to be deleted`)

| IDTA 02035-6 attribute                                                                                 | Our model                                                           | Reason / status                                                                                                 |
| ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| BatteryChemistry (ShortName, ClearName)                                                                | kept, mandatory — both sub-fields**marked "#to be deleted"** | purely for battery manufacturers                                                                                |
| BatteryMaterials — batteryMaterialLocation                                                            | kept, mandatory —**marked "#to be deleted"**                 | Deletion under discussion: option "entire material" / "not applicable" to be checked with the chemical industry |
| BatteryMaterials — batteryMaterialIdentifier (CAS number), batteryMaterialName, isCriticalRawMaterial | kept, mandatory                                                     | Unchanged from IDTA                                                                                             |
| BatteryMaterials — batteryMaterialMass                                                                | kept, optional                                                      | Optional in IDTA as well                                                                                        |
| HazardousSubstances — hazardousSubstanceName, hazardousSubstanceIdentifier                            | kept, mandatory                                                     | Unchanged from IDTA                                                                                             |
| HazardousSubstances — hazardousSubstanceClass, hazardousSubstanceConcentration                        | kept, optional                                                      | Optional in IDTA as well                                                                                        |
| HazardousSubstances — hazardousSubstanceImpact                                                        | kept, optional —**marked "#to be deleted"**                  | Inline comment in the working file (line 87)                                                                    |
| HazardousSubstances — hazardousSubstanceLocation                                                      | kept, optional —**marked "#to be deleted"**                  | Inline comment in the working file (line 88);                                                                   |
| Location structure (ComponentName, ComponentId)                                                        | kept, optional —**marked "#to be deleted"**                  | Inline comments in the working file (lines 217, 223);                                                           |

## Simplified Model

```
MaterialComposition
 ├─ BatteryChemistry
 │   ├─ ShortName                                  #to be deleted
 │   └─ ClearName                                  #to be deleted
 ├─ BatteryMaterials[]        (one entry per material)
 │   ├─ batteryMaterialLocation                    #to be deleted
 │   ├─ batteryMaterialIdentifier (CAS number)
 │   ├─ batteryMaterialName
 │   ├─ batteryMaterialMass                        (optional)
 │   └─ isCriticalRawMaterial
 └─ HazardousSubstances[]     (one entry per substance)
     ├─ hazardousSubstanceClass                    (optional)
     ├─ hazardousSubstanceName
     ├─ hazardousSubstanceIdentifier
     ├─ hazardousSubstanceConcentration            (optional)
     ├─ hazardousSubstanceImpact                   (optional)   #to be deleted
     └─ hazardousSubstanceLocation                 (optional)   #to be deleted
         └─ location = ComponentName / ComponentId (optional)   #to be deleted
```
