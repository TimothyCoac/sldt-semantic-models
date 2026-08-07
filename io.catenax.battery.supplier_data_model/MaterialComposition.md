# Part 6 – Material Composition: Supplier Model vs. IDTA 02035-6

deletions are **marked** (`#to be deleted`)

| IDTA 02035-6 attribute                                                                                 | Our model                                                           | Reason / status                                                                                                 |
| ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| BatteryChemistry (ShortName, ClearName)                                                                | kept, optional | purely for battery manufacturers                                                                                |
| BatteryMaterials — batteryMaterialLocation                                                            | kept, optional              | Deletion under discussion: option "entire material" / "not applicable" to be checked with the chemical industry |
| BatteryMaterials — batteryMaterialIdentifier (CAS number), batteryMaterialName, isCriticalRawMaterial | kept, mandatory                                                     | Unchanged from IDTA                                                                                             |
| BatteryMaterials — batteryMaterialMass                                                                | kept, optional                                                      | Optional in IDTA as well                                                                                        |
| HazardousSubstances — hazardousSubstanceName, hazardousSubstanceIdentifier                            | kept, mandatory                                                     | Unchanged from IDTA                                                                                             |
| HazardousSubstances — hazardousSubstanceClass, hazardousSubstanceConcentration                        | kept, optional                                                      | Optional in IDTA as well                                                                                        |
| HazardousSubstances — hazardousSubstanceImpact                                                        | kept, optional                | Inline comment in the working file (line 87)                                                                    |
| HazardousSubstances — hazardousSubstanceLocation                                                      | kept, optional                  | Inline comment in the working file (line 88);                                                                   |
| Location structure (ComponentName, ComponentId)                                                        | kept, optional                 | Inline comments in the working file (lines 217, 223);                                                           |

## Simplified Model

```
MaterialComposition
 ├─ BatteryChemistry
 │   ├─ ShortName                                  (optional)
 │   └─ ClearName                                  (optional)
 ├─ BatteryMaterials[]        (one entry per material)
 │   ├─ batteryMaterialLocation                    (optional)
 │   ├─ batteryMaterialIdentifier (CAS number)
 │   ├─ batteryMaterialName
 │   ├─ batteryMaterialMass                        (optional)
 │   └─ isCriticalRawMaterial
 └─ HazardousSubstances[]     (one entry per substance)
     ├─ hazardousSubstanceClass                    (optional)
     ├─ hazardousSubstanceName
     ├─ hazardousSubstanceIdentifier
     ├─ hazardousSubstanceConcentration            (optional)
     ├─ hazardousSubstanceImpact                   (optional)
     └─ hazardousSubstanceLocation                 (optional)
         └─ location = ComponentName / ComponentId (optional)
```
