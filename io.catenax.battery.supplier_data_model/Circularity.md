# Part 7 – Circularity: Supplier Model vs. IDTA 02035-7

**Irrelevant** = battery-item / economic-operator level; a supplier cannot know or declare it.

| IDTA 02035-7 attribute                                                                       | Our model                 | Reason                                                                                                                                                                                                                                                |
| -------------------------------------------------------------------------------------------- | ------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| RecycledContentInformation (per material: material, pre-consumer share, post-consumer share) | **kept, mandatory** | The Commission clarified that carbon footprint, recycled content and due diligence information will not be required from February 2027.These requirements will become applicable at a later stage under their respective legal provisions. 
| RenewableContent                                                                             | **kept, mandatory**  |(https://teams.microsoft.com/l/message/19:meeting_ZjJmNDg4MjktNTM4My00ODVmLWIxMWUtMjRmODRmYmIyOTVm@thread.v2/1786092732355?context=%7B%22contextType%22%3A%22chat%22%7D)                                                                                                                                                                                                                |
| DismantlingAndRemovalInformation                                                             | **kept, optional**                  | **Irrelevant** — battery-pack level (EO); postponed by two years;                                                                                                                                                                             |
| SparePartSources                                                                             | **kept, optional**                  | **Irrelevant** — spare-part directory of the battery is compiled by the EO                                                                                                                                                                     |
| SafetyMeasures                                                                               | **kept, optional**  | Referenced directly from IDTA 02035-7 as-is. Note: battery-level content (extinguishing agents, waste-battery handling) is EO territory; supplier-side safety statements also live with the substance data in Part 6.                                 |
| EndOfLifeInformation                                                                         | **kept, optional**                  | **Irrelevant** — end-user information duty of the producer (Battery Regulation Art. 60)                                                                                                                                                        |

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
