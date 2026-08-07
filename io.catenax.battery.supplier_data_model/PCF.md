# Part 3 – Product Carbon Footprint: Supplier Model vs. IDTA 02035-3


| IDTA 02035-3 attribute                        | Our model                                             | Reason / status                                                                                                                                                              |
| --------------------------------------------- | ----------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ProductCarbonFootprints (list of PCF entries) | kept, mandatory                                       | Unchanged from IDTA                                                                                                                                                          |
| pcfCalculationMethods                         | kept, mandatory                                       | Unchanged; referenced from the generic IDTA carbon footprint model, as in the original                                                                                       |
| pcfCo2eq                                      | kept, mandatory                                       | Unchanged. Board note: "Full Product PCF"                                                                                                                                    |
| referenceImpactUnitForCalculation             | kept, mandatory                                       | Unchanged from IDTA                                                                                                                                                          |
| quantityOfMeasureForCalculation               | kept, mandatory                                       | Unchanged from IDTA                                                                                                                                                          |
| lifeCyclePhases                               | kept, optional                                    | OEMs recommended to keep "Life cycle stages in", however, discussions still ongoing on the differences between PCF section in Battery pass and PCF industry standard from Catena-X. |
| performanceClass                              | kept, mandatory                                       | Unchanged from IDTA                                                                                                                                                          |
| webLinkToPublicCarbonFootprintStudy           | kept, optional | Optional as relevance for suppliers along the value chain is difficult to determine                                                                                                                                               |

## Simplified Model

```
CarbonFootprintBattery
 └─ ProductCarbonFootprints[]        (one entry per PCF declaration)
     ├─ PcfCalculationMethods
     ├─ PcfCo2eq                                  (note: "Full Product PCF")
     ├─ ReferenceImpactUnitForCalculation
     ├─ QuantityOfMeasureForCalculation
     ├─ PerformanceClass
     └─ WebLinkToPublicCarbonFootprintStudy       #to be deleted?
```
