Part 1 – Digital Nameplate: Supplier Model vs. IDTA 02035-1

**CX** = already carried by Catena-X Industry Core (CX-0126 part type / CX-0127 part instance & batch);
**Irrelevant** = battery-item / economic-operator level; a supplier cannot know or declare it.

| IDTA 02035-1 attribute                | Our model                                        | Reason                                                                                                                                                                                                                                                                                                          |
| ------------------------------------- | ------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| URIOfTheProduct                       | removed                                          | **CX** — manufacturerPartId (CX-0126/0127) → [PartTypeInformation](https://github.com/eclipse-tractusx/sldt-semantic-models/blob/main/io.catenax.part_type_information/1.0.0/PartTypeInformation.ttl)                                                                                                    |
| SerialNumber                          | removed                                          | **CX** — localIdentifiers "partInstanceId" (CX-0127) → [SerialPart](https://github.com/eclipse-tractusx/sldt-semantic-models/blob/main/io.catenax.serial_part/3.0.1/SerialPart.ttl)                                                                                                                      |
| ManufacturerIdentifier                | removed                                          | **CX** — localIdentifiers "manufacturerId" = BPNL (CX-0127) → [SerialPart](https://github.com/eclipse-tractusx/sldt-semantic-models/blob/main/io.catenax.serial_part/3.0.1/SerialPart.ttl) / [Batch](https://github.com/eclipse-tractusx/sldt-semantic-models/blob/main/io.catenax.batch/3.0.1/Batch.ttl) |
| DateOfManufacture                     | removed                                          | **CX** — manufacturingInformation.date (CX-0127) → [SerialPart](https://github.com/eclipse-tractusx/sldt-semantic-models/blob/main/io.catenax.serial_part/3.0.1/SerialPart.ttl) / [Batch](https://github.com/eclipse-tractusx/sldt-semantic-models/blob/main/io.catenax.batch/3.0.1/Batch.ttl)            |
| DateOfPuttingIntoService              | removed                                          | **Irrelevant** — happens downstream, after delivery                                                                                                                                                                                                                                                      |
| BatteryStatus (life-cycle stage)      | removed                                          | **Irrelevant** — status of the finished battery, set by the economic operator                                                                                                                                                                                                                            |
| OperatorIdentifier                    | removed                                          | **Irrelevant** — identifies the party placing the battery on the market                                                                                                                                                                                                                                  |
| ManufacturerName                      | **kept, mandatory**                        | Referenced as-is from IDTA 02035-1. identifies the supplier as legal entity                                                                                                                                                                                                                                     |
| UniqueFacilityIdentifier              | **kept, mandatory**                        | Referenced as-is from IDTA 02035-1. Manufacturing site identification (e.g. BPN-S);                                                                                                                                                                                                                             |
| AddressInformation                    | **kept, optional**                         | Referenced as-is from IDTA 02035-1 (which builds on digital_nameplate 3.0.0 / contact_information 1.0.0) -> not optional in IDTA                                                                                                                                                                                |
| Markings                              | **kept, optional**                         | Referenced as-is from IDTA 02035-1 (marking structure from shared:Markings).                                                                                                                                                                                                                                    |
| EUDeclarationOfConformity             | **kept, optional**                         | Referenced as-is from IDTA 02035-1. Supplier-side DoCs conceivable                                                                                                                                                                                                                                              |
| ResultsOfTestReportsProvingCompliance | **kept, optional**                         | Referenced as-is from IDTA 02035-1. Supplier counterpart = certificates of analysis / material test certificates.                                                                                                                                                                                               |
| – (not in IDTA)                      | BatchOrLotIdentifier —**added, optional** | Own property (no IDTA ancestor).                                                                                                                                                                                                                                                                               |

## Simplified Model

```
SupplierNameplate
 ├─ ManufacturerName
 ├─ AddressInformation                          (optional)
 │   └─ IDTA address structure
 │       ├─ Street
 │       ├─ ZipCode
 │       ├─ CityTown
 │       ├─ NationalCode
 │       └─ Company / Phone / Email / ...      (optional)
 ├─ UniqueFacilityIdentifier
 ├─ BatchOrLotIdentifier                        (optional, added — not in IDTA)
 ├─ Markings[]                                  (optional)
 │   └─ Marking
 │       ├─ MarkingName
 │       ├─ MarkingFile
 │       ├─ DesignationOfCertificateOrApproval
 │       ├─ IssueDate
 │       ├─ ExpiryDate
 │       └─ MarkingAdditionalText
 ├─ EUDeclarationOfConformity[]                 (optional, document IDs → Part 2)
 └─ ResultsOfTestReportsProvingCompliance[]     (optional, document IDs → Part 2)
```
