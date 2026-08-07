# Part 1 – Digital Nameplate: Supplier Model vs. IDTA 02035-1

All 13 IDTA properties are kept and referenced as-is; only optional/mandatory is adjusted. The custom addition BatchOrLotIdentifier was removed.

| IDTA 02035-1 attribute                     | Our model           | Note                                                                                     |
| ------------------------------------------ | ------------------- | ---------------------------------------------------------------------------------------- |
| URIOfTheProduct                            | **mandatory** | mandatory                                                                                |
| SerialNumber                               | optional            | optional                                                                                 |
| ManufacturerIdentifier                     | **mandatory** | BPNL                                                                                     |
| DateOfManufacture                          | optional            | relevance for suppliers along the value chain difficult to determine                     |
| DateOfPuttingIntoService                   | optional            | optional in IDTA/Catena-X as well                                                        |
| BatteryStatus (payload "LifeCycleStage")   | optional            | not relevant for suppliers                                                               |
| OperatorIdentifier                         | optional            | optional in IDTA/Catena-X as well                                                        |
| ManufacturerName                           | **mandatory** | mandatory -> relevant for suppliers                                                                                     |
| UniqueFacilityIdentifier                   | optional            | not relevant for OEMs to receive from suppliers for the battery passport                 |
| AddressInformation                         | optional            | not relevant for OEMs to receive from suppliers for the battery passport                 |
| Markings                                   | optional            | –                                                                                       |
| EUDeclarationOfConformity                  | optional            | not relevant for OEMs; if background information is needed, add in one of the sub models |
| ResultsOfTestReportsProvingCompliance      | optional            | –                                                                                       |
| BatchOrLotIdentifier (custom, not in IDTA) | **removed**   | custom addition removed                                                                  |

## Simplified Model

```
SupplierNameplate
 ├─ URIOfTheProduct                        (mandatory)
 ├─ SerialNumber                           (optional)
 ├─ ManufacturerIdentifier                 (mandatory, BPNL)
 ├─ DateOfManufacture                      (optional)
 ├─ DateOfPuttingIntoService               (optional)
 ├─ BatteryStatus                          (optional, payload "LifeCycleStage")
 ├─ OperatorIdentifier                     (optional)
 ├─ ManufacturerName                       (mandatory, relevant for suppliers)
 ├─ UniqueFacilityIdentifier               (optional)
 ├─ AddressInformation                     (optional)
 ├─ Markings                               (optional)
 ├─ EUDeclarationOfConformity              (optional, document IDs → Handover Documentation)
 └─ ResultsOfTestReportsProvingCompliance  (optional, document IDs → Handover Documentation)
```
