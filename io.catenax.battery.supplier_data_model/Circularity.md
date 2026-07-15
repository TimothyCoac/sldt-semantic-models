# Part 7 – Circularity: Supplier Model vs. IDTA 02035-7

**Irrelevant** = battery-item / economic-operator level; a supplier cannot know or declare it.


| IDTA 02035-7 attribute                                                                       | Our model                 | Reason                                                                                                                                                                                                                                                |
| -------------------------------------------------------------------------------------------- | ------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| RecycledContentInformation (per material: material, pre-consumer share, post-consumer share) | **kept, mandatory** | Core supplier circularity content. Referenced as-is from IDTA 02035-7 ([property in Circularity_shared.ttl](https://github.com/admin-shell-io/smt-semantic-models/blob/main/io.admin-shell.idta.batterypass.circularity/1.0.0/Circularity_shared.ttl)) |
| RenewableContent                                                                             | **kept, optional**  | Referenced as-is from IDTA 02035-7.                                                                                                                                                                                                                   |
| DismantlingAndRemovalInformation                                                             | removed                   | **Irrelevant** — battery-pack level (EO); postponed by two years;                                                                                                                                                                             |
| SparePartSources                                                                             | removed                   | **Irrelevant** — spare-part directory of the battery is compiled by the EO                                                                                                                                                                     |
| SafetyMeasures                                                                               | **kept, optional**  | Referenced directly from IDTA 02035-7 as-is. Note: battery-level content (extinguishing agents, waste-battery handling) is EO territory; supplier-side safety statements also live with the substance data in Part 6.                                 |
| EndOfLifeInformation                                                                         | removed                   | **Irrelevant** — end-user information duty of the producer (Battery Regulation Art. 60)                                                                                                                                                        |


## Simplified Model

```
SupplierCircularity
 ├─ RecycledContentInformation[]      (mandatory, one entry per material)
 │   ├─ RecycledMaterial              (Cobalt | Nickel | Lithium | Lead)
 │   ├─ PreConsumerShare              (0–100 % of the material)
 │   └─ PostConsumerShare             (0–100 % of the material)
 ├─ RenewableContent                  (optional, 0–100 % of total mass)
 └─ SafetyMeasures                    (optional, referenced from IDTA as-is:
     ├─ SafetyInstructions[]           document identifiers → Part 2
     └─ ExtinguishingAgents[]          fire classes)
```
