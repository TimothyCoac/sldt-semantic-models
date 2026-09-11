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
This standard is intended for organizations supplying materials, components, or cells to battery producers and for organizations receiving such information to create the Battery Passport.
### Data Providers
Data Providers are actors in the battery value chain that supply Battery Passport-relevant information to other actors. A Data Provider may be any organization that holds and shares relevant data, regardless of its position in the value chain.
It should be noted that the battery production supply chain may involve a wider range of supplier types than the three categories described above.
  
### Data Consumers
Data Consumers are actors in the battery value chain that request, receive, and use supplier information for Battery Passport creation, regulatory compliance, or any organization that requires Battery Passport-relevant data from another actor in the value chain.
Examples include:
- Battery Manufacturers
- Battery Producers acting as Economic Operators under the EU Battery Regulation
- Tier-1 suppliers collecting data from material producers or other upstream suppliers
  
# 1 INTRODUCTION

Battery Passports require information originating from multiple actors throughout the battery value chain. While battery producers remain responsible for creating and publishing Battery Passports, a substantial share of the underlying information originates from upstream suppliers. This standard establishes a mechanism for exchanging supplier-generated information through Catena-X Digital Twins and standardized semantic models.

The objective is to:
- Create a common understanding of which information is needed throughout the value chain to create Battery Passports 
- Define standardized data models to reduce complexity, redundancy and facilitate implementation throughout the whole value chain
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

### 1.6 DIGITAL TWINS AND SPECIFIC ASSET IDs
For generally relevant specific asset IDs, the Policy Constraints the [Base standard](./CX-0160-BatteryPassport-base.md) MUST be followed.

### 1.7 POLICY CONSTRAINTS FOR DATA EXCHANGE

For Policies, the Policy Constraints in the [Base standard](./CX-0160-BatteryPassport-base.md) MUST be followed.

# 2 Roles, Responsibilities and Process Description

This chapter specifies the process for providing Battery Passport-relevant data from a Data Provider to a Data Consumer within the Catena-X Dataspace.

## 2.1 Data Provider

A Data Provider is any actor in the battery value chain that makes Battery Passport-relevant data available to another actor. The Data Provider may be an upstream supplier, a component manufacturer, a material producer, or any other organization providing relevant information.
The Data Provider:
- MUST provide all mandatory information applicable to its supplied product.
- MUST ensure accuracy and completeness of provided information.
- SHOULD update information when significant product changes occur.
- MAY provide optional information when contractually agreed.

## 2.2 Data Consumer

A Data Consumer is any actor in the battery value chain that receives Battery Passport-relevant data from another actor and uses it for passport generation, compliance, or related business processes. The Data Consumer may also act as a Data Provider in other exchanges.

The Data Consumer:
- MUST retrieve information through Catena-X compatible interfaces (Catena-X Standards which need to be followed, like CX-0002, CX-0018, CX-0151, CX-0152).
- MAY combine information from multiple suppliers.
- MAY enrich supplier information with additional data.

## 2.3 PROCESS REPRESENTATION

This process applies where Battery Passport-relevant information originates from a supplier and is required by another actor in the battery value chain for the creation, maintenance, or provision of Battery Passport information.

The Data Provider makes relevant data available to the Data Consumer using the semantic models and exchange mechanisms defined by this standard. The Data Consumer retrieves and processes the provided information and may combine it with information obtained from other Data Providers and from its own systems.

### DATA PROVIDER'S RESPONSIBILITIES

The data provider MUST create the assets and digital twins as described in Chapter 1 [1.6 DIGITAL TWINS AND SPECIFIC ASSET IDs](###16-digital-twins-and-specific-asset-ids) and [5 APPLICATION PROGRAMMING INTERFACES](#5-application-programming-interfaces) in order to provide battery passport information to the data consumer.
The aspect models for each battery MUST be created in accordance with [chapter 4](#4-semantic-models).

The data provider SHOULD make the digital twins available to the data consumer in a timely manner after production of the battery.
The data provider and data consumer MAY agree on any other point in time.

### DATA CONSUMER'S RESPONSIBILITIES

The data consumer MUST use the Application Programming Interfaces as described in [chapter 4](#4-application-programming-interfaces) to retrieve battery passport information from the data provider.

The data consumer can create the assets and digital twins as described in chapters [2.1.1 DIGITAL TWINS AND SPECIFIC ASSET IDs](#211-digital-twins-and-specific-asset-ids) and [5 APPLICATION PROGRAMMING INTERFACES](#5-application-programming-interfaces) to provide the battery passport to other participants within the Catena-X dataspace.

The data consumer needs to provide the battery passport to external stakeholders as required by regulation.

## 2.4 REQUESTING BATTERY PASSPORT DATA

See the [Base standard](./CX-0160-BatteryPassport-base.md) for the requesting of Battery Passport Data .

The data provider SHOULD implement notifications.
The data consumer MAY implement notifications.


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

## 4 SEMANTIC MODELS

> *This section is normative*

For a list of semantic models relevant for the use case consider the  [Base standard](./CX-0160-BatteryPassport-base.md).

### Required Models

The Digital Nameplate data model (IDTA-02035-1) MUST be provided together with one or more optional submodels. The selection of the applicable optional submodel(s) SHALL be agreed bilaterally between the Data Provider and the Data Consumer.

The Digital Nameplate is intended to provide a common, industry-independent information basis for the identification and description of an asset. This approach enables the Digital Nameplate information to be used within the IDTA framework, where no industry-specific core information model comparable to the Catena-X industry core is defined.

All data models Handover Documentation, Technical Data, Material Composition, Circularity, Carbon Footprint for Battery Passport MAY be provided, and subject to bilateral discussions

The following semantic models MUST be provided on Type Level:

- Digital Battery Passport - Part 2: Handover Documentation (IDTA-02035-2)
- Digital Battery Passport - Part 4: Technical Data (IDTA-02035-4)
- Digital Battery Passport - Part 6: Material Composition (IDTA-02035-6)
- Digital Battery Passport - Part 7: Circularity (IDTA-02035-7)

The following semantic models MUST be provided on Instance Level:

- Digital Battery Passport - Part 1: Digital Nameplate (IDTA-02035-1)
- Digital Battery Passport - Part 3: Carbon Footprint for Battery Passport (IDTA-02035-3) - as soon as delegation act for PCF calculation for batteries is available

> [!Note]
> Although the semantic models are identical, the data itself cannot be used as a direct copy by the party responsible for composing the battery passport: it is merely input data used to compose the complete battery passport.
>
>- a) update with their own information (example: white labelling)
>- b) add information that cannot be provided by the supplier (example: operatorID)
>- c) add or update dynamic data (Product Condition IDTA-02035-5)
>
> and
>
>- d) add other missing or incomplete data points
>- e) re-calculate or extending Carbon Footprint data: depending on the calculation method additional values need to be considered, for example data related to logistics
>- f) add and update instance related documents in Handover Documentation (example: information on accidents)

For further details the [Base standard](./CX-0160-BatteryPassport-base.md) MUST be considered.

## 5 APPLICATION PROGRAMMING INTERFACES

> *This section is normative*

### 5.1 APIs ASSOCIATED WITH DIGITAL TWINS

This standard completely and solely builds upon the standard [CX-0002](https://catenax-ev.github.io/docs/next/standards/CX-0002-DigitalTwinsInCatenaX) Digital Twins in Catena-X.

For more details consider the [Base standard](./CX-0160-BatteryPassport-base.md).

### 5.2 NOTIFICATIONS

Implementing the Notification API of the Base standard is RECOMMENDED for the data provider; the data consumer MAY implement it.

For more details consider the [Base standard](./CX-0160-BatteryPassport-base.md).

## 6 REFERENCES

### 6.1 NORMATIVE REFERENCES

> *This section is normative*

- CX-0002 Digital Twins in Catena-X v2.4.0
- CX-0018 Dataspace Connectivity v4.2
- CX-0126 Industry Core: PartType 2.1.1
- CX-0127 Industry Core: Part Instance 2.0.2
- CX-0151 Industry Core: Basics v1.0.0
- CX-0152 Policy Constraints for Data Exchange v1.0.0

### 6.2 NON-NORMATIVE REFERENCES

> *This section is non-normative*

- [DIN DKE SPEC 99100:2025-02](https://www.dinmedia.de/en/technical-rule/din-dke-spec-99100/385692321)
- [Batterypass Semantic Models: Aspect Models](https://github.com/admin-shell-io/smt-semantic-models/releases/tag/V1.1)
- [Batterypass Semantic Models: Submodel Template Specifications](https://github.com/admin-shell-io/submodel-templates/tree/main/published/Digital%20Battery%20Passport)
- [Digital Battery Passport: Use Case Guideline of the Asset Administraion Shell](https://industrialdigitaltwin.org/wp-content/uploads/2026/02/IDTA_Catena-X_Guideline_Digital_Battery_Passport.pdf), Guideline, Feb. 2026.
- EN 18216:2026: Digital product passport - Data exchange protocols
- EN 18219:2026: Digital product passport - Unique identifiers
- EN 18220:2026: Digital product passport - Data Carriers
- EN 18221:2026: Digital product passport - Data storage, archiving, and data persistence
- EN 18222:2026: Digital Product Passport - Application Programming Interfaces (APIs) for the product passport lifecycle management and searchability
- EN 18223:2026: Digital Product Passport - System interoperability
- prEN 18239:2025: Digital Product Passport - Access rights management, information system security, and business confidentiality
- prEN 18246:2025: Digital product passport - Data authentication, reliability and integrity
- [Regulation (EU) 2023/1542 of the European Parliament and of the Council of 12 July 2023 concerning batteries and waste batteries, amending Directive 2008/98/EC and Regulation (EU) 2019/1020 and repealing Directive 2006/66/EC](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32023R1542) - referenced as "Battery Regulation".
- [Regulation (EU) 2024/1781 of the European Parliament and of the Council of 13 June 2024 establishing a framework for the setting of ecodesign requirements for sustainable products, amending Directive (EU) 2020/1828 and Regulation (EU) 2023/1542 and repealing Directive 2009/125/EC (Text with EEA relevance)](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A02024R1781-20240628) - referenced as "Ecodesign for Sustainable Products Regulation" or "ESPR".

### 6.3 REFERENCE IMPLEMENTATIONS

There is currently no actively maintained reference application.
