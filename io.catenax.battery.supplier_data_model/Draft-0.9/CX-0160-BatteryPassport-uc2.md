# CX-0160-X Supplier Data Management: Provisioning of Battery Passport Relevant Data by Tier-1 Suppliers
## ABSTRACT
This standard is an extension of the CX-0160 Battery Passport Data Management standards. It specifies how Tier-1 suppliers provide Battery Passport relevant information to battery producers within the Catena-X ecosystem. The standard applies to suppliers that provide products directly to battery producers, including:
- Material Suppliers
- Component Suppliers
- Cell Producers
  
Unlike battery producers, suppliers covered by this standard are not responsible for publishing a Battery Passport or Digital Product Passport (DPP). The purpose of this standard is to ensure that battery producers receive harmonized, machine-readable, and interoperable data contributions that can be incorporated into Battery Passport generation processes.

This standard defines:
- Roles and responsibilities
- Digital twins and semantic models
- Data exchange mechanisms
- Applicability rules
- Mandatory and optional information requirements by supplier role
---
## FOR WHOM IS THE STANDARD DESIGNED
This standard is intended for organizations supplying materials, components, or cells directly to battery producers.
### Data Providers
Data Providers are Tier-1 suppliers that contribute Battery Passport relevant information to battery producers.
It should be noted that the battery production supply chain may involve a wider range of supplier types than the three categories described above. Nevertheless, during the development of this standard, consideration was limited to these three roles, due to availability and interest of the participants. The standard may apply to additional Tier-1s as well after careful consideration.
  
### Data Consumers
Data Consumers are battery producers that collect supplier information for Battery Passport creation and regulatory compliance.
Examples include:
- Battery Manufacturers
- Battery Producers acting as Economic Operators under the EU Battery Regulation
---

# 1 INTRODUCTION

Battery Passports require information originating from multiple actors throughout the battery value chain. While battery producers remain responsible for creating and publishing Battery Passports, a substantial share of the underlying information originates from upstream suppliers. This standard establishes a mechanism for exchanging supplier-generated information through Catena-X Digital Twins and standardized semantic models.

The objective is to:
- Reduce manual reporting efforts
- Improve interoperability across the value chain
- Support battery producers to publish DPPs
- Enable traceable sustainability and product information exchange
This standard does not transfer regulatory responsibility from battery producers to suppliers. Instead, it defines a common framework through which suppliers can provide the information required by battery producers to fulfil their obligations.

---

## 1.1 AUDIENCE & SCOPE

_This section is non-normative_
This standard is relevant for the following Catena-X roles:

### Data Provider
A Tier-1 supplier directly supplying products to battery producers.
### Data Consumer
A Battery Producer receiving supplier data contributions.

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
- Battery producer to OEM data exchange.
- Exchange with non-Catena-X ecosystems.
- Provisioning of downstream Battery Passport information.
- Dynamic product condition information occurring after handover to the battery producer.
---
## 1.2 CONTEXT AND ARCHITECTURE FIT

_This section is non-normative_

The Supplier Data Model forms an upstream extension of the Catena-X Battery Passport ecosystem.
Tier-1 suppliers provide information required by battery producers to:
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

A Data Provider is a supplier directly supplying products to a battery producer.
The Data Provider:
- MUST provide all mandatory information applicable to its supplied product.
- MUST ensure accuracy and completeness of provided information.
- SHOULD update information when significant product changes occur.
- MAY provide optional information when contractually agreed.
---

## 2.2 Data Consumer

A Data Consumer is a battery producer receiving supplier information.

The Data Consumer:
- MUST retrieve information through Catena-X compatible interfaces.
- MAY combine information from multiple suppliers.
- MAY enrich supplier information with additional data.
- REMAINS RESPONSIBLE for Battery Passport creation and publication.
---

# 3 PRINCIPLES FOR DATA OBLIGATION DEFINITION

_This section is normative_
Supplier obligations differ from Battery Producer obligations because suppliers are not responsible for publishing a Battery Passport.
Data obligations SHALL therefore be determined based on applicability and ownership of information.
## 3.1 Criterion 1: Product Applicability
A data element is mandatory only when applicable to the supplied product.
Examples:
- Battery Chemistry Information is relevant only for Cell Producers, as a battery chemistry name cannot be defined for individual chemical products or components supplied to a battery.
- Location of Hazardous Substances is applicable only to Components and Cell Producers, and not to chemical products, as it is not possible to define where within a chemical product (e.g., a chemical supplied in a bottle) a hazardous substance is located.

---
## 3.2 Criterion 2: Supplier Role
Obligations depend on the role of the supplier.
### Material Supplier
Typically provides:
- Material identification information
- Material composition information
- Carbon Footprint information
- Circularity related information

### Component Supplier
Typically provides:
- Component identification information
- Material composition information
- Carbon Footprint information
- Product documentation
  
### Cell Producer
Typically provides:
- Cell identification information
- Battery Chemistry information
- Material composition information
- Carbon Footprint information
- Circularity information
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
## 3.4 Criterion 4: Regulatory Relevance
Information required to support compliance with the EU Battery Regulation SHOULD be prioritized.
Examples include:
- Product Carbon Footprint
- Hazardous Substance Information
- Critical Raw Material Information
- Renewable Content Information
---

# 4 OBLIGATION CLASSIFICATION MODEL
_This section is normative_

To maintain alignment with Catena-X and IDTA principles, data requirements within this standard SHALL be classified according to one of the obligation categories defined below. The classification determines the expected level of data provision by the respective supplier role.
### 4.1 Obligation Categories
| Classification | Definition |
|----------------|------------|
| **Mandatory** | The attribute MUST be provided by the supplier for the relevant supplier role. |
| **Conditional Mandatory** | The attribute MUST be provided when defined applicability criteria are fulfilled, such as regulatory relevance, product characteristics, or supplier-specific responsibilities. |
| **Optional** | The attribute MAY be provided by the supplier but is not required for conformance with this standard. |
| **Not Applicable (N/A)** | The attribute is not relevant to the supplier role and therefore does not need to be provided. |

### 4.2 Determination of Obligations

The obligation level of an attribute SHALL be determined based on the following criteria:

1. **Supplier Role**
- Material Supplier
- Component Supplier
- Cell Producer
2. **Product Applicability**
- Whether the attribute is relevant to the supplied product.
3. **Data Ownership**
- Whether the supplier is the authoritative source of the information.
4. **Regulatory Relevance**
- Whether the information is required to support compliance with applicable regulations, including Regulation (EU) 2023/1542.
### 4.3 Example Classification
The table below illustrates how obligation levels may differ between supplier roles.

| Attribute | Material Supplier | Component Supplier | Cell Producer |
|------------|------------------|-------------------|--------------|
| URIOfTheProduct | Mandatory | Mandatory | Mandatory |
| Battery Chemistry | N/A | N/A | Mandatory |
| Recycled Content | Conditional Mandatory | Conditional Mandatory | Conditional Mandatory |
| PcfCo2eq | Mandatory | Mandatory | Mandatory |
| End Of Life Information | Optional | Optional | Optional |
 
### 4.4 Use of Conditional Mandatory Attributes
Conditional Mandatory attributes are expected to represent a significant portion of supplier-provided data because the applicability of Battery Passport information varies substantially across supplier types and products.
Examples include:
- Recycled content information when recycled or critical raw materials are present.
- EU Declaration of Conformity when legally required for the supplied product.
- Battery chemistry information when the supplied product is a battery cell.
- Material-specific information that is only available to the supplier responsible for the material.
This approach enables a harmonized and scalable implementation of supplier data exchange while recognizing the differing responsibilities of Material Suppliers, Component Suppliers, and Cell Producers.

---

# 5 SEMANTIC MODELS
_This section is normative_
The following semantic models are supported by this standard.
## 5.1 Supplier Nameplate
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
# 6 ROLE-SPECIFIC OBLIGATION PRINCIPLE
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
