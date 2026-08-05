# Part 3 – Product Carbon Footprint: Supplier Model vs. IDTA 02035-3


| IDTA 02035-3 attribute                        | Our model                                             | Reason / status                                                                                                                                                              |
| --------------------------------------------- | ----------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ProductCarbonFootprints (list of PCF entries) | kept, mandatory                                       | Unchanged from IDTA                                                                                                                                                          |
| pcfCalculationMethods                         | kept, mandatory                                       | Unchanged; referenced from the generic IDTA carbon footprint model, as in the original                                                                                       |
| pcfCo2eq                                      | kept, mandatory                                       | Unchanged. Board note: "Full Product PCF"                                                                                                                                    |
| referenceImpactUnitForCalculation             | kept, mandatory                                       | Unchanged from IDTA                                                                                                                                                          |
| quantityOfMeasureForCalculation               | kept, mandatory                                       | Unchanged from IDTA                                                                                                                                                          |
| lifeCyclePhases                               | **removed**                                     | In-file comment: only one cradle-to-gate PCF is relevant for the OEM, which will be mapped into "A1 – raw material supply". Miro comment: "Deleted! Only full PCF relevant" |
| performanceClass                              | kept, mandatory                                       | Unchanged from IDTA                                                                                                                                                          |
| webLinkToPublicCarbonFootprintStudy           | kept, mandatory —**deletion under discussion** | Miro comment: "To be deleted?"                                                                                                                                               |

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
