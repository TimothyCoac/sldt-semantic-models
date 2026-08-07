# Part 2 – Handover Documentation: Supplier Model vs. IDTA 02035-2

**Irrelevant** = battery-item / economic-operator level; a supplier cannot know or declare it.

| IDTA 02035-2 attribute                                                     | Our model                 | Reason                                                                                                                                                                                        |
| -------------------------------------------------------------------------- | ------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Documents (set: identifiers, classifications, versions with digital files) | **kept, mandatory** | Referenced as-is from[IDTA 02035-2](https://github.com/admin-shell-io/smt-semantic-models/blob/main/io.admin-shell.idta.batterypass.handover_documentation/1.0.0/HandoverDocumentation.ttl).  |

## Simplified Model

```
SupplierHandoverDocumentation
 └─ Documents[]
     └─ per document:
         ├─ DocumentIds[]              (Domain, Identifier, IsPrimary?)
         ├─ DocumentClassifications[]  (ClassId, ClassName, System; ≥1 per VDI 2770)
         └─ DocumentVersions[]         (min 1)
             ├─ Language[]             (min 1)
             ├─ Version (opt) / Title / Subtitle (opt) / Description (opt)
             └─ DigitalFiles[]         (min 1: link + MIME type; ≥1 PDF/A)
```
