# CX-0160-2 Supplier Data Management: Provisioning of Battery Passport Relevant Data by Suppliers
## ABSTRACT
This standard is an extension to the CX-0160 Battery Passport Data Management standards. It is part of a series for multiple use cases, covering Use Case (2): **Provisioning of Battery Passport Relevant Data by Suppliers**. The standard applies to suppliers that provide products to battery producers, including but not limited to:
- Material Suppliers
- Component Suppliers
- Cell Producers
  
Unlike battery producers, suppliers covered by this standard are not responsible for publishing a Battery Passport or Digital Product Passport (DPP). The purpose of this standard is to ensure that battery producers receive harmonized, machine-readable, and interoperable data contributions that can be incorporated into Battery Passport generation processes.
The standard specifies roles and responsibilities, digital twins and semantic models, mandatory and optional information requirements by supplier role, and APIs and processes required for the data provider to share battery instance and battery type data with the data consumer. 

## DISCLAIMER
This standard defines five submodels for the provisioning of Battery Passport relevant data by suppliers: Nameplate, Handover Documentation, Product Carbon Footprint, Circularity and Material Composition.

Only the Supplier "Nameplate" submodel is mandatory. It MUST be provided by every supplier role covered by this standard (Material Supplier, Component Supplier, Cell Producer) to ensure compatibility with the IDTA Battery Passport submodel templates. The remaining sub models (Handover Documentation, Product Carbon Footprint, Supplier Circularity, Material Composition) are optional. Whether they are provided, and in which scope, is subject to bilateral (B2B) agreement between Data Provider and Data Consumer.

The obligation levels defined in Sections 3 to 6 (Mandatory or Optional) refer to attributes within a submodel. They apply only once the exchange of the respective submodel has been agreed between the parties. An attribute classified as mandatory within an optional submodel is therefore only mandatory if that submodel is provided. 

## FOR WHOM IS THE STANDARD DESIGNED
This standard is intended for organizations supplying materials, components, or cells to battery producers.
### Data Providers
Data Providers are actors in the battery value chain that supply Battery Passport-relevant information to other actors. A Data Provider may be any organization that holds and shares relevant data, regardless of its position in the value chain.
It should be noted that the battery production supply chain may involve a wider range of supplier types than the three categories described above. Nevertheless, during the development of this standard, consideration was limited to these three roles, due to availability and interest of the participants.
  
### Data Consumers
Data Consumers are actors in the battery value chain that request, receive, and use supplier information for Battery Passport creation, regulatory compliance, or any organization that requires Battery Passport-relevant data from another actor in the value chain.
Examples include:
- Battery Manufacturers
- Battery Producers acting as Economic Operators under the EU Battery Regulation
- Tier-1 suppliers collecting data from material producers or other upstream suppliers
  
# 1 INTRODUCTION

Battery Passports require information originating from multiple actors throughout the battery value chain. While battery producers remain responsible for creating and publishing Battery Passports, a substantial share of the underlying information originates from upstream suppliers. This standard establishes a mechanism for exchanging supplier-generated information through Catena-X Digital Twins and standardized semantic models.

The objective is to:
- Reduce manual reporting efforts
- Improve interoperability across the value chain
- Protecting business confidentiality via controlled data access
- Support battery producers to publish DPPs
- Enable traceable sustainability and product information exchange

This standard does not transfer regulatory responsibility from battery producers to suppliers. Instead, it defines a common framework through which suppliers can provide the information required by battery producers to fulfil their obligations.


## 1.1 AUDIENCE & SCOPE

_This section is non-normative_
This standard is relevant for the following Catena-X roles:

### Data Provider
An actor supplying materials or products within the battery value chain.
### Data Consumer
An actor in the battery value chain that receives battery passport relevant data.

This standard specifies how supplier-related Battery Passport information is modeled, provisioned, discovered and accessed within the Catena-X Dataspace.

The **standard applies to**, but is not limited to, the following entities:

- Materials used in battery production
- For component supplier integration, for example housing
- Battery cells supplied to battery producers

The standard **shall be applied** when:

- Providing Battery Passport relevant information to battery producers.
- Providing sustainability, compliance and traceability information required for Battery Passport generation.
- Exchanging supplier-owned data through Catena-X Digital Twins.

The standard is **not intended to be applied** for:

- Publishing Battery Passports.
- Publishing Digital Product Passports.
- Battery producer to OEM data exchange.
- Exchange with non-Catena-X ecosystems.
- Provisioning of downstream Battery Passport information.
- Dynamic product condition information occurring after handover to the battery producer.
- For non‑battery product passports or use cases outside the battery domain (see CX-0143)
- For full regulatory-compliance e.g. for providing public information without access-restrictions. The standard may enable it, but as Catena-X is an ecosystem with a focus on trust and identification this is out of scope for the actual specification.
  
## 1.2 CONTEXT AND ARCHITECTURE FIT

_This section is non-normative_

The Supplier Data Model forms an upstream extension of the Catena-X Battery Passport ecosystem.
Suppliers provide information required by battery producers to:
- Create Battery Passports.
- To reduce manual effort from data collection.
- Establish material and product traceability.

Information exchanged under this standard represents supplier contributions and does not necessarily correspond directly to the final Battery Passport values published by the battery producer. Battery producers may:
- Aggregate supplier data.
- Enrich information with additional data sources.
- Perform Battery Passport specific calculations.
- Add missing information.
- Recalculate sustainability metrics where required.
This standard therefore defines the supplier contribution layer within the Battery Passport architecture.

The standard is not intended to include all potentially relevant information for every downstream use case and also not focusing on the provisioning to non-Catena-X members. Instead, it establishes the core semantic, structural, and architectural foundation on which further domain‑specific or proprietary data products can be built. Data owners may add complementary information _(as mentioned above)_ via additional aspect models all governed by Catena‑X‑compliant access and usage policies to ensure privacy, security, and data sovereignty.

This standard is currently not harmonized with the IDTA standardization regarding the Battery Passport (see [Semantic Models](#3-semantic-models) section), This is due to the adaptation of certain attributes defined as mandatory in the joint (Catena-X & IDTA) battery pass data model to optional attributes within the Catena-X standard, where these attributes are not applicable to the respective value chain participants.
Harmonization with IDTA to be initiated after 26.09 release. Any required updates to the Catena-X standard will be addressed as part of the subsequent 27.03 release, in alignment with and subject to agreement with the relevant IDTA Working Group.

## 1.3 CONFORMANCE

_This section is non-normative_
Sections marked as non-normative as well as all authoring guidelines, diagrams, examples, and notes in this specification are non-normative. Everything else in this specification is normative.

The key words **MAY**, **MUST**, **MUST NOT**, **OPTIONAL**, **RECOMMENDED**, **REQUIRED**, **SHOULD** and **SHOULD NOT** in this document are to be interpreted as described in BCP 14 [RFC2119] [RFC8174] when, and only when, they appear in all capitals, as shown here.

All participants and their solutions will need to prove, that they are conform with the Catena-X standards.
To validate that the standards are applied correctly, Catena-X employs Conformity Assessment Bodies (CABs). Conformity to this standard must be demonstrated along the conformity assessment criteria (CACs) defined for this use case.

### 1.4 EXAMPLES

> *This section is non-normative*

The example in the [Base standard](./CX-0160-BatteryPassport-base.md) can be followed to understand the exchange of battery-related information across the automotive battery value chain within the Catena-X ecosystem.

### 1.5 TERMINOLOGY

> *This section is non-normative*

For terminology refer to the [Base standard](./CX-0160-BatteryPassport-base.md) and to the glossary: https://catenax-ev.github.io/glossary.

# 2 ROLES AND RESPONSIBILITIES

## 2.1 Data Provider

A Data Provider is any actor in the battery value chain that makes Battery Passport-relevant data available to another actor. The Data Provider may be an upstream supplier, a component manufacturer, a material producer, or any other organization providing relevant information.
The Data Provider:
- MUST provide all mandatory information applicable to its supplied product.
- MUST ensure accuracy and completeness of provided information.
- SHOULD update information when significant product changes occur.
- MAY provide optional information when contractually agreed.
---

## 2.2 Data Consumer

A Data Consumer is any actor in the battery value chain that receives Battery Passport-relevant data from another actor and uses it for passport generation, compliance, or related business processes. The Data Consumer may also act as a Data Provider in other exchanges.

The Data Consumer:
- MUST retrieve information through Catena-X compatible interfaces.
- MAY combine information from multiple suppliers.
- MAY enrich supplier information with additional data.
- REMAINS RESPONSIBLE for Battery Passport creation and publication.
---

# 3 PRINCIPLES FOR DATA OBLIGATION DEFINITION

_This section is normative_
Supplier obligations differ from Battery Producer obligations because suppliers are not responsible for publishing a Battery Passport.
Data obligations SHALL therefore be determined based on "Supplier's role" in the value chain.

## 3.1 Criterion 1: Product Applicability
A data element is mandatory only when applicable to the supplied product.
Examples:
- Battery Chemistry Information is relevant only for Cell Producers, as a battery chemistry name cannot be defined for individual chemical products or components supplied to a battery.
- Location of Hazardous Substances is applicable only to Components and Cell Producers, and not to chemical products, as it is not possible to define where within a chemical product a hazardous substance is located.

---
## 3.2 Criterion 2: Supplier Role
Data submission obligations depend on the supplier’s role. The table below provides an overview of which attributes are mandatory and which are optional for material suppliers, component suppliers, and cell producers.


| Sub Model                     | Field Name                                                                  | IDTA Model Obligation | Supplier Data Model Obligation (Overall) | Material Supplier Obligation | Component Supplier Obligation | Cell Producer to Batteries Obligation | Comments                                                                                                                                                                                                                                                                                                                   |
| ----------------------------- | --------------------------------------------------------------------------- | --------------------- | ---------------------------------------- | ---------------------------- | ----------------------------- | ------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| SupplierNameplate             | URIOfTheProduct                                                             | mandatory             | mandatory                                | mandatory                    | mandatory                     | mandatory                             |                                                                                                                                                                                                                                                                                                                            |
| SupplierNameplate             | SerialNumber                                                                | mandatory             | optional                                 | optional                     | optional                      | optional                              | Optional, as this information is not applicable at Instance level for all sub models and for all value chain partners. It becomes applicable where data related to serialized parts is exchanged.                                                                                                                          |
| SupplierNameplate             | ManufacturerIdentifier                                                      | mandatory             | mandatory                                | mandatory                    | mandatory                     | mandatory                             |                                                                                                                                                                                                                                                                                                                            |
| SupplierNameplate             | DateOfManufacture                                                           | mandatory             | optional                                 | optional                     | optional                      | optional                              | This information may not be available or applicable to all value chain partners (e.g., material suppliers). It shall be provided where requested by the data consumer and where available in the data provider's master data.                                                                                              |
| SupplierNameplate             | DateOfPuttingIntoService                                                    | optional              | optional                                 | optional                     | optional                      | optional                              | This information may not be applicable to all value chain partners (e.g., for chemical materials, the date of putting into service becomes available only when the material is sold for the first time). It shall be provided where requested by the data consumer and where available in the data provider's master data. |
| SupplierNameplate             | LifeCycleStage                                                              | mandatory             | optional                                 | optional                     | optional                      | optional                              | Applicable to battery manufacturers, usually applicable to products in a battery value chain that larger than a cell.                                                                                                                                                                                                      |
| SupplierNameplate             | OperatorIdentifier                                                          | optional              | optional                                 | optional                     | optional                      | optional                              | For battery manufactureres, unless specifically requested from data consumer                                                                                                                                                                                                                                               |
| SupplierNameplate             | ManufacturerName                                                            | mandatory             | mandatory                                | mandatory                    | mandatory                     | mandatory                             |                                                                                                                                                                                                                                                                                                                            |
| SupplierNameplate             | UniqueFacilityIdentifier                                                    | mandatory             | optional                                 | optional                     | optional                      | optional                              | Optional for upstream value chain partners to reduce implementation complexity. Facility-level information shall be provided where requested by the data consumer. For example, a facility identifier may be required to enable PCF reporting at Instance level.                                                           |
| SupplierNameplate             | AddressInformation                                                          | mandatory             | optional                                 | optional                     | optional                      | optional                              | Optional where a BPNL and/or BPNS is provided, as the respective business partner and/or site can be identified through the BPN.                                                                                                                                                                                           |
| SupplierNameplate             | Markings                                                                    | mandatory             | optional                                 | optional                     | optional                      | optional                              | Applicable to battery manufacturers only.                                                                                                                                                                                                                                                                                  |
| SupplierNameplate             | EUDeclarationOfConformity                                                   | mandatory             | optional                                 | optional                     | mandatory                     | mandatory                             | Optional, as this information is not applicable to all products exchanged along the value chain. It is commonly applicable to products subject to CE marking requirements.                                                                                                                                                 |
| SupplierNameplate             | ResultsOfTestReportsProvingCompliance                                       | mandatory             | optional                                 | optional                     | optional                      | optional                              | Applicable to battery manufacturers only.                                                                                                                                                                                                                                                                                  |
| SupplierHandoverDocumentation | Documents                                                                   | mandatory             | mandatory                                | mandatory                    | mandatory                     | mandatory                             |                                                                                                                                                                                                                                                                                                                            |
| CarbonFootprintBattery        | PcfCalculationMethods                                                       | mandatory             | mandatory                                | mandatory                    | mandatory                     | mandatory                             |                                                                                                                                                                                                                                                                                                                            |
| CarbonFootprintBattery        | PcfCo2eq                                                                    | mandatory             | mandatory                                | mandatory                    | mandatory                     | mandatory                             |                                                                                                                                                                                                                                                                                                                            |
| CarbonFootprintBattery        | ReferenceImpactUnitForCalculation                                           | mandatory             | mandatory                                | mandatory                    | mandatory                     | mandatory                             |                                                                                                                                                                                                                                                                                                                            |
| CarbonFootprintBattery        | QuantityOfMeasureForCalculation                                             | mandatory             | mandatory                                | mandatory                    | mandatory                     | mandatory                             |                                                                                                                                                                                                                                                                                                                            |
| CarbonFootprintBattery        | LifeCyclePhases (Raw material, manufacturing/production, logistics and EoL) | mandatory             | mandatory                                | mandatory                    | mandatory                     | mandatory                             |                                                                                                                                                                                                                                                                                                                            |
| CarbonFootprintBattery        | PerformanceClass                                                            | mandatory             | optional                                 | optional                     | optional                      | optional                              | Applicable for battery manufacturers only.                                                                                                                                                                                                                                                                                 |
| CarbonFootprintBattery        | WebLinkToPublicCarbonFootprintStudy                                         | mandatory             | optional                                 | optional                     | optional                      | optional                              | Applicable to battery manufacturers. Performance classes are not defined for all products across the value chain. For example, performance classes may not be applicable to chemical materials. Therefore, this attribute is optional.                                                                                     |
| Circularity                   | RecycledContentInformation                                                  | mandatory             | mandatory                                | mandatory                    | mandatory                     | mandatory                             | If you have CRMs in your material / product then declaring recycled contetn becomes mandatory                                                                                                                                                                                                                              |
| Circularity                   | RenewableContent                                                            | mandatory             | mandatory                                | mandatory                    | mandatory                     | mandatory                             | Reporting of recycled content is mandatory where the product contains Critical Raw Materials. Where no Critical Raw Materials are contained in the product, this attribute is not applicable.                                                                                                                              |
| Circularity                   | DismantlingAndRemovalInformation                                            | mandatory             | optional                                 | optional                     | optional                      | optional                              |                                                                                                                                                                                                                                                                                                                            |
| Circularity                   | SparePartSources                                                            | mandatory             | optional                                 | optional                     | optional                      | optional                              | Applicable for battery manufacturers only.                                                                                                                                                                                                                                                                                 |
| Circularity                   | SafetyMeasures                                                              | mandatory             | optional                                 | optional                     | optional                      | optional                              | Applicable to battery manufacturers. The information shall also be provided by other value chain partners where explicitly requested by the data consumer, e.g., where a component supplier is required to provide information on spare parts.                                                                             |
| Circularity                   | EndOfLifeInformation                                                        | mandatory             | optional                                 | optional                     | optional                      | optional                              | Optional, unless explicitly requested by the data consumer. This information is also typically provided in the precautionary statements section of the Safety Data Sheet (SDS) and may therefore be omitted where it is already available through the SDS                                                                  |
| Material Composition          | Battery Chemistry                                                           | mandatory             | optional                                 | optional                     | optional                      | optional                              | Optional, unless explicitly requested by the data consumer.                                                                                                                                                                                                                                                                |
| Material Composition          | BatteryChemistry.ShortName                                                  | mandatory             | optional                                 | optional                     | optional                      | mandatory                             |                                                                                                                                                                                                                                                                                                                            |
| Material Composition          | BatteryChemistry.ClearName                                                  | mandatory             | optional                                 | optional                     | optional                      | mandatory                             | Applicable to battery manufacturers and cell producers only. Not applicable to other value chain partners.                                                                                                                                                                                                                 |
| Material Composition          | BatteryMaterials.batteryMaterialLocation                                    | mandatory             | optional                                 | optional                     | optional                      | optional                              |                                                                                                                                                                                                                                                                                                                            |
| Material Composition          | BatteryMaterials.batteryMaterialIdentifier                                  | mandatory             | mandatory                                | mandatory                    | mandatory                     | mandatory                             |                                                                                                                                                                                                                                                                                                                            |
| Material Composition          | BatteryMaterials.batteryMaterialName                                        | mandatory             | mandatory                                | mandatory                    | mandatory                     | mandatory                             | Applicable for battery manufacturers only.                                                                                                                                                                                                                                                                                 |
| Material Composition          | BatteryMaterials.isCriticalRawMaterial                                      | mandatory             | mandatory                                | mandatory                    | mandatory                     | mandatory                             |                                                                                                                                                                                                                                                                                                                            |
| Material Composition          | BatteryMaterials.batteryMaterialMass                                        | optional              | optional                                 | optional                     | optional                      | optional                              | Optional, consistent with the corresponding attribute in the original Joint Battery Passport Model between Catena-X and IDTA                                                                                                                                                                                               |
| Material Composition          | HazardousSubstances.hazardousSubstanceName                                  | mandatory             | mandatory                                | mandatory                    | mandatory                     | mandatory                             |                                                                                                                                                                                                                                                                                                                            |
| Material Composition          | HazardousSubstances.hazardousSubstanceIdentifier                            | mandatory             | mandatory                                | mandatory                    | mandatory                     | mandatory                             |                                                                                                                                                                                                                                                                                                                            |
| Material Composition          | HazardousSubstances — hazardousSubstanceClass                               | optional              | optional                                 | optional                     | optional                      | optional                              | Optional, consistent with the corresponding attribute in the original Joint Battery Passport Model between Catena-X and IDTA                                                                                                                                                                                               |
| Material Composition          | HazardousSubstances — hazardousSubstanceConcentration                       | optional              | optional                                 | optional                     | optional                      | optional                              | Optional, consistent with the corresponding attribute in the original Joint Battery Passport Model between Catena-X and IDTA                                                                                                                                                                                               |
| Material Composition          | HazardousSubstances — hazardousSubstanceImpact                              | optional              | optional                                 | optional                     | optional                      | optional                              | Optional, consistent with the corresponding attribute in the original Joint Battery Passport Model between Catena-X and IDTA                                                                                                                                                                                               |
| Material Composition          | HazardousSubstances — hazardousSubstanceLocation                            | optional              | optional                                 | optional                     | optional                      | optional                              | Optional, consistent with the corresponding attribute in the original Joint Battery Passport Model between Catena-X and IDTA                                                                                                                                                                                               |
| Material Composition          | Location structure (ComponentName, ComponentId)                             | mandatory             | optional                                 | optional                     | optional                      | optional                              | Applicable for battery manufacturers only.                         

---
## 3.3 Criterion 3: Data Ownership
Information SHALL only be mandatory when the supplier is the authoritative source of the information.
Examples of supplier-owned information:
- Product Carbon Footprint
- Material composition
- Renewable content
- Compliance documents

Examples of information not owned by suppliers:
- Battery-level assessments
- Vehicle-specific information
- Post-production product condition information
---

# 4 SEMANTIC MODELS
_This section is normative_
The following semantic models are supported by this standard.
## 4.1 Supplier Nameplate
Supplier Nameplate contains general identification information about the supplied product and supplier.
### Mandatory
- URIOfTheProduct
- ManufacturerIdentifier
- ManufacturerName
### Conditional Mandatory
- EUDeclarationOfConformity
- SerialNumber
- DateOfManufacture
- LifeCycleStage
### Optional
- DateOfPuttingIntoService
- OperatorIdentifier
- AddressInformation
- Markings
- ResultsOfTestReportsProvingCompliance
- UniqueFacilityIdentifier
---
## 4.2 Supplier Handover Documentation
Supplier Handover Documentation contains documents exchanged together with supplier data.
### Mandatory
- Documents (when documents are available)
### Optional
- Additional supporting documentation
---
## 4.3 Carbon Footprint
The Carbon Footprint model provides Product Carbon Footprint information for supplied products.
### Mandatory
- PcfCalculationMethods
- PcfCo2eq
- ReferenceImpactUnitForCalculation
- QuantityOfMeasureForCalculation
### Optional
- LifeCyclePhases
- PerformanceClass
- WebLinkToPublicCarbonFootprintStudy
---
## 4.4 Supplier Circularity
Supplier Circularity contains information related to circular economy requirements.
### Mandatory
- RenewableContent
### Conditional Mandatory
- RecycledContentInformation when recycled content or critical raw materials are present.
### Optional
- DismantlingAndRemovalInformation
- SparePartSources
- SafetyMeasures

- EndOfLifeInformation
---
## 4.5 Material Composition
Material Composition contains information about materials, substances, and battery chemistry where applicable.
### Mandatory for all supplier categories
- Material Identifier (e.g. CAS Number)
- Material Name
- Critical Raw Material Indicato
- Hazardous Substance Name
- Hazardous Substance Identifier
 
### Mandatory for Cell Producers
- BatteryChemistry.ShortName
- BatteryChemistry.ClearName
### Optional
- Material Mass
- Material Location
- Hazardous Substance Class
- Hazardous Substance Concentration
- Hazardous Substance Impact
- Hazardous Substance Location
- Component Structure Information
---
# 5 ROLE-SPECIFIC OBLIGATION PRINCIPLE
The final obligation matrix SHALL be maintained separately and classify all data elements for the following supplier roles:
- Material Supplier
- Component Supplier
- Cell Producer
Each attribute SHALL be assigned one of the following obligation levels:
- Mandatory
- Conditional Mandatory
- Optional
- Not Applicable

The obligation matrix SHALL serve as the normative reference for determining supplier-specific reporting obligations.
 
469
This approach allows alignment with existing Battery Passport semantic models while ensuring that supplier obligations remain limited to information that is relevant, applicable, and owned by the supplier.
