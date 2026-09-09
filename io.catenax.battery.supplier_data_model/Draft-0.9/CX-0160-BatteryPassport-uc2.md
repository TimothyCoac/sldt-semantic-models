# CX-0160-X Supplier Data Management: Provisioning of Battery Passport relevant Data
## ABSTRACT
This standard is an extension of the CX-0160 Battery Passport Data Management standard. It specifies how suppliers provide Battery Passport relevant information to battery producers or Tier-N suppliers within the Catena-X ecosystem. The standard applies to suppliers that provide products to battery producers, including, but not limited to:
- Material Suppliers
- Component Suppliers
- Cell Producers
  
Unlike battery producers, suppliers covered by this standard are not responsible for publishing a Battery Passport or Digital Product Passport (DPP). The purpose of this standard is to ensure that battery producers receive harmonized, machine-readable, and interoperable data contributions that can be incorporated into Battery Passport generation processes. It also aims at simplifying interfaces and creating a common understanding along the value chain what information are needed and how the attributes are interpreted.


## DISCLAIMER
This standard defines five submodels for the provisioning of Battery Passport relevant data by suppliers: Supplier Nameplate, Supplier Handover Documentation, Product Carbon Footprint, Supplier Circularity and Material Composition.

Only the Supplier Nameplate submodel is mandatory. (AKE: I would disagree as discussed yesterday.) It MUST be provided by every supplier role covered by this standard (Material Supplier, Component Supplier, Cell Producer, and others) to ensure compatibility with the IDTA Battery Passport submodel templates. (AKE: Why is this relevant? The submodels are the same just with different optional/mandatory attributes. Using the nameplate datamodel will not ensure compatibility.)

The remaining submodels (Supplier Handover Documentation, Product Carbon Footprint, Supplier Circularity, Material Composition) are optional. Whether they are provided, and in which scope, is subject to bilateral (B2B) agreement between Data Provider and Data Consumer. 

## FOR WHOM IS THE STANDARD DESIGNED
This standard is intended for organizations supplying materials, components, or cells to battery producers and for organizations receiving such information to create the Battery Passport.

### Data Providers
Data Providers are actors in the battery value chain that supply Battery Passport relevant information to other actors. A Data Provider may be any organization that holds and shares relevant data, regardless of its position in the value chain.
It should be noted that the battery production supply chain may involve a wider range of supplier types than the three categories described above. 
  
### Data Consumers
Data Consumers are actors in the battery value chain that request, receive, and use supplier information for Battery Passport creation, regulatory compliance, or any organization that requires Battery Passport relevant data from another actor in the value chain.
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

The standard applies to:
- Materials used in battery production
- Components supplied to battery producers
- Battery cells supplied to battery producers

The standard shall be applied when:

- Providing Battery Passport relevant information to battery producers.
- Providing sustainability, compliance and traceability information required for Battery Passport generation.
- Exchanging supplier-owned data through Catena-X Digital Twins.

The standard is not intended to be applied for:

- Publishing Battery Passports.
- Publishing Digital Product Passports.
- Battery producer to OEM data exchange. (AKE: Why not? This is exactly our use case.)
- Exchange with non-Catena-X ecosystems.
- Provisioning of downstream Battery Passport information.
- Dynamic product condition information occurring after handover to the battery producer.
---
## 1.2 CONTEXT AND ARCHITECTURE FIT

_This section is non-normative_

The Supplier Data Model forms an upstream extension of the Catena-X Battery Passport ecosystem.
Suppliers provide information required by battery producers to:
- Create Battery Passports.
- To reduce manual effort from data collection.
- Establish material and product traceability.

Information exchanged under this standard represents supplier contributions and does not necessarily correspond directly to the final Battery Passport values published by the battery producer.
Battery producers may:
- Aggregate supplier data.
- Enrich information with additional data sources.
- Perform Battery Passport specific calculations.
- Add missing information.
- Recalculate sustainability metrics where required.
This standard therefore defines the supplier contribution layer within the Battery Passport architecture.

---

## 1.3 CONFORMANCE

_This section is non-normative_
Sections marked as non-normative, examples, notes and explanatory text are non-normative.
The key words **MUST**, **MUST NOT**, **OPTIONAL**, **RECOMMENDED**, **REQUIRED**, **SHOULD**, and **SHOULD NOT** in this document are to be interpreted as described in RFC 2119 and RFC 8174. All participants and solutions claiming compliance with this standard MUST demonstrate conformance against applicable conformity assessment criteria.

---

# 2 ROLES AND RESPONSIBILITIES

## 2.1 Data Provider

A Data Provider is any actor in the battery value chain that makes Battery Passport-relevant data available to another actor. The Data Provider may be an upstream supplier, a component manufacturer, a material producer, or any other organization providing relevant information.
The Data Provider: (AKE: I would delete the bullet points. No added value)
- MUST provide all mandatory information applicable to its supplied product. (AKE: You cannot write it like this. This has 0 impact on technical implementation)
- MUST ensure accuracy and completeness of provided information. (AKE: Is this really something we need to mention or that we can enforce?)
- SHOULD update information when significant product changes occur.
- MAY provide optional information when contractually agreed. 
---

## 2.2 Data Consumer

A Data Consumer is any actor in the battery value chain that receives Battery Passport-relevant data from another actor and uses it for passport generation, compliance, or related business processes. The Data Consumer may also act as a Data Provider in other exchanges.

The Data Consumer:
- MUST retrieve information through Catena-X compatible interfaces. (AKE: Obvious. Preferrably reference the other Catena-X Standards which need to be followed, like CX-0002, CX-0018, CX-0151, CX-0152 etc.)
- MAY combine information from multiple suppliers.
- MAY enrich supplier information with additional data.
- REMAINS RESPONSIBLE for Battery Passport creation and publication. (AKE: No. The consumer could also be a Tier-1 supplier which aggregates PCF values and sends it to an economic operator.)
---

# 3 PRINCIPLES FOR DATA OBLIGATION DEFINITION

_This section is normative_
Supplier obligations differ from Battery Producer obligations because suppliers are not responsible for publishing a Battery Passport.
Data obligations SHALL therefore be determined based on "Supplier's role" in the value chain. (AKE: How do you define the role of a supplier within the value chain? I think this is too complicated and leaves a lot of room for excluding parties we do not know of. I would just make 2 data models. The economic operator must use the IDTA data models and all other participants who want to share information to another supplier or the economic operator, they can use the IDTA optional data models. Don't overload yourself with too much complexity.)

## 3.1 Criterion 1: Product Applicability
A data element is mandatory only when applicable to the supplied product. (AKE: That cannot be technically enforced and therefore I would not define it like that. Also the interpretation of what is mandatory for a supplied product might differ between two parties. This sentence seems to specify things but it doesnt. I think this standard should be a technical standard with the focus of creation a common understanding about the attributes and the way they have to be transmitted.)
Examples:
- Battery Chemistry Information is relevant only for Cell Producers, as a battery chemistry name cannot be defined for individual chemical products or components supplied to a battery.
- Location of Hazardous Substances is applicable only to Components and Cell Producers, and not to chemical products, as it is not possible to define where within a chemical product a hazardous substance is located.

---
## 3.2 Criterion 2: Supplier Role
Data submission obligations depend on the supplier’s role. The table below provides an overview of which attributes are mandatory and which are optional for material suppliers, component suppliers, and cell producers. (AKE: Are you 100% sure this applies to those supplier types? If not, leave it flexible.)


| Sub Model                     | Field Name                                                                  | IDTA Model Obligation | Supplier Data Model Obligation (Overall) | Material Supplier Obligation | Component Supplier Obligation | Cell Producer to Batteries Obligation | Comments                                                                                      |
| ----------------------------- | --------------------------------------------------------------------------- | --------------------- | ---------------------------------------- | ---------------------------- | ----------------------------- | ------------------------------------- | --------------------------------------------------------------------------------------------- |
| SupplierNameplate             | URIOfTheProduct                                                             | mandatory             | mandatory                                | mandatory                    | mandatory                     | mandatory                             |                                                                                               |
| SupplierNameplate             | SerialNumber                                                                | mandatory             | optional                                 | optional                     | optional                      | optional                              |                                                                                               |
| SupplierNameplate             | ManufacturerIdentifier                                                      | mandatory             | mandatory                                | mandatory                    | mandatory                     | mandatory                             |                                                                                               |
| SupplierNameplate             | DateOfManufacture                                                           | mandatory             | optional                                 | optional                     | optional                      | optional                              |                                                                                               |
| SupplierNameplate             | DateOfPuttingIntoService                                                    | optional              | optional                                 | optional                     | optional                      | optional                              |                                                                                               |
| SupplierNameplate             | LifeCycleStage                                                              | mandatory             | optional                                 | optional                     | optional                      | optional                              |                                                                                               |
| SupplierNameplate             | OperatorIdentifier                                                          | optional              | optional                                 | optional                     | optional                      | optional                              |                                                                                               |
| SupplierNameplate             | ManufacturerName                                                            | mandatory             | mandatory                                | mandatory                    | mandatory                     | mandatory                             |                                                                                               |
| SupplierNameplate             | UniqueFacilityIdentifier                                                    | mandatory             | optional                                 | optional                     | optional                      | optional                              |                                                                                               |
| SupplierNameplate             | AddressInformation                                                          | mandatory             | optional                                 | optional                     | optional                      | optional                              |                                                                                               |
| SupplierNameplate             | Markings                                                                    | mandatory             | optional                                 | optional                     | optional                      | optional                              |                                                                                               |
| SupplierNameplate             | EUDeclarationOfConformity                                                   | mandatory             | optional                                 | optional                     | mandatory                     | mandatory                             | Commonly required for products that carry a CE marking.                                       |
| SupplierNameplate             | ResultsOfTestReportsProvingCompliance                                       | mandatory             | optional                                 | optional                     | optional                      | optional                              |                                                                                               |
| SupplierHandoverDocumentation | Documents                                                                   | mandatory             | mandatory                                | mandatory                    | mandatory                     | mandatory                             |                                                                                               |
| CarbonFootprintBattery        | PcfCalculationMethods                                                       | mandatory             | mandatory                                | mandatory                    | mandatory                     | mandatory                             |                                                                                               |
| CarbonFootprintBattery        | PcfCo2eq                                                                    | mandatory             | mandatory                                | mandatory                    | mandatory                     | mandatory                             |                                                                                               |
| CarbonFootprintBattery        | ReferenceImpactUnitForCalculation                                           | mandatory             | mandatory                                | mandatory                    | mandatory                     | mandatory                             |                                                                                               |
| CarbonFootprintBattery        | QuantityOfMeasureForCalculation                                             | mandatory             | mandatory                                | mandatory                    | mandatory                     | mandatory                             |                                                                                               |
| CarbonFootprintBattery        | LifeCyclePhases (Raw material, manufacturing/production, logistics and EoL) | mandatory             | optional                                 | optional                     | optional                      | optional                              |                                                                                               |
| CarbonFootprintBattery        | PerformanceClass                                                            | mandatory             | optional                                 | optional                     | optional                      | optional                              | mandatory?                                                                                    |
| CarbonFootprintBattery        | WebLinkToPublicCarbonFootprintStudy                                         | mandatory             | optional                                 | optional                     | optional                      | optional                              |                                                                                               |
| Circularity                   | RecycledContentInformation                                                  | mandatory             | mandatory                                | mandatory                    | mandatory                     | mandatory                             | If you have CRMs in your material / product then declaring recycled content becomes mandatory |
| Circularity                   | RenewableContent                                                            | mandatory             | mandatory                                | mandatory                    | mandatory                     | mandatory                             |                                                                                               |
| Circularity                   | DismantlingAndRemovalInformation                                            | mandatory             | optional                                 | optional                     | optional                      | optional                              |                                                                                               |
| Circularity                   | SparePartSources                                                            | mandatory             | optional                                 | optional                     | optional                      | optional                              |                                                                                               |
| Circularity                   | SafetyMeasures                                                              | mandatory             | optional                                 | optional                     | optional                      | optional                              |                                                                                               |
| Circularity                   | EndOfLifeInformation                                                        | mandatory             | optional                                 | optional                     | optional                      | optional                              |                                                                                               |
| Material Composition          | Battery Chemistry                                                           | mandatory             | optional                                 | optional                     | optional                      | optional                              |                                                                                               |
| Material Composition          | BatteryChemistry.ShortName                                                  | mandatory             | optional                                 | optional                     | optional                      | mandatory                             |                                                                                               |
| Material Composition          | BatteryChemistry.ClearName                                                  | mandatory             | optional                                 | optional                     | optional                      | mandatory                             |                                                                                               |
| Material Composition          | BatteryMaterials.batteryMaterialLocation                                    | mandatory             | optional                                 | optional                     | optional                      | optional                              |                                                                                               |
| Material Composition          | BatteryMaterials.batteryMaterialIdentifier                                  | mandatory             | mandatory                                | mandatory                    | mandatory                     | mandatory                             |                                                                                               |
| Material Composition          | BatteryMaterials.batteryMaterialName                                        | mandatory             | mandatory                                | mandatory                    | mandatory                     | mandatory                             |                                                                                               |
| Material Composition          | BatteryMaterials.isCriticalRawMaterial                                      | mandatory             | mandatory                                | mandatory                    | mandatory                     | mandatory                             |                                                                                               |
| Material Composition          | BatteryMaterials.batteryMaterialMass                                        | optional              | optional                                 | optional                     | optional                      | optional                              |                                                                                               |
| Material Composition          | HazardousSubstances.hazardousSubstanceName                                  | mandatory             | mandatory                                | mandatory                    | mandatory                     | mandatory                             |                                                                                               |
| Material Composition          | HazardousSubstances.hazardousSubstanceIdentifier                            | mandatory             | mandatory                                | mandatory                    | mandatory                     | mandatory                             |                                                                                               |
| Material Composition          | HazardousSubstances — hazardousSubstanceClass                               | optional              | optional                                 | optional                     | optional                      | optional                              |                                                                                               |
| Material Composition          | HazardousSubstances — hazardousSubstanceConcentration                       | optional              | optional                                 | optional                     | optional                      | optional                              |                                                                                               |
| Material Composition          | HazardousSubstances — hazardousSubstanceImpact                              | optional              | optional                                 | optional                     | optional                      | optional                              |                                                                                               |
| Material Composition          | HazardousSubstances — hazardousSubstanceLocation                            | optional              | optional                                 | optional                     | optional                      | optional                              |                                                                                               |
| Material Composition          | Location structure (ComponentName, ComponentId)                             | mandatory             | optional                                 | optional                     | optional                      | optional                              |                                                                                               |

---
## 3.3 Criterion 3: Data Ownership
Information SHALL only be mandatory when the supplier is the authoritative source of the information. (AKE: Again. Nothing technical)
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

# 5 SEMANTIC MODELS
_This section is normative_
The following semantic models are supported by this standard. (AKE: There need to be links to the data models within the catena-x data models. If those models should be published in TX it should be here: https://github.com/eclipse-tractusx/sldt-semantic-models Also the urn, ttl-file, json-schema etc is missing. Someone has to create all those files and create a PR in order for Johann/TC4S to review the data models.)
## 5.1 Supplier Nameplate
Supplier Nameplate contains general identification information about the supplied product and supplier.
### Mandatory
- URIOfTheProduct
- ManufacturerIdentifier
- ManufacturerName
### Conditional Mandatory (AKE. Rephrase.)
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
## 5.2 Supplier Handover Documentation
Supplier Handover Documentation contains documents exchanged together with supplier data.
### Mandatory
- Documents (when documents are available)
### Optional
- Additional supporting documentation
---
## 5.3 Carbon Footprint
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
## 5.4 Supplier Circularity
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
## 5.5 Material Composition
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


AKE: 
What's missing from my point of view:
1. Context and architecture fit: How do you creat the twins, on what level and how does the consumer know that there is a new one to pull the data? Maybe even a sequence diagram.
2. Conformance and proof of conformity aka CAC.md. How can 3 third party evaluate that someone (data consumer, data provider or solution provider (which has not at all been talked about) is following this standard and be certified?)
3. List of Standards which need to be followed like e.g.
CX-0001 Participant Agent Registration v1.2
CX-0018 Dataspace Connectivity v4.1.1
CX-0127 Industry Core: Part Instance v2.0.2
CX-0151 Industry Core: Basics v1.0.0
CX-0152 Policy Constraints for Data Exchange v1.0.0
4. Does this use case get a new policy which is defined by Daniela Wuensch and documented in the CX-0152?
5. Data Models are unsufficiently described just with mandatory and optional. I find it hard to implement a data model without any of the relevant files. To say use the IDTA data model but make it optional is a very optimistic approach that this is going to work.
6. Please be aware of all the questions they are going to ask you once you are creating the Pull request on the main branch of the standardization. See here e.g. https://github.com/catenax-eV/product-standardization-prod/pull/594 
I was also involved in the ECU Standard which you can find here: https://github.com/catenax-eV/product-standardization-prod/blob/R26.06-release-bundle/standards/CX-0161-ECUCryptoMaterial/CX-0161-ECUCryptoMaterial.md 
We have received quite good feedback on it and maybe it can help as a guideline as well.
