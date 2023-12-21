# Interlynk CycloneDX Property Taxonomy

This is the official listing of Interlynk's CycloneDX property namespace and taxonomy. The document lists all reserved properties, however the actual SBOM may use a subset of these depending on the product type and environment.

See [CycloneDX official documentation](https://github.com/CycloneDX/cyclonedx-property-taxonomy) for additional details.

## `interlynk`

| Namespace                 | Description                                               |
| --------------------------| --------------------------------------------------------- |
| `interlynk:sbom`          | Namespace for SBOM document level properties              |
| `interlynk:metadata`      | Namespace for SBOM metadata level properties              |
| `interlynk:component`     | Namespace for properties associated with a component      |
| `interlynk:service`       | Namespace for properties associated with a service        |
| `interlynk:vulnerability` | Namespace for properties associated with a vulnerability  |


## `interlynk:sbom`

| Property Name                          | Description                                                  |
| ---------------------------------------| -------------------------------------------------------------|
| `interlynk:sbom:engine_version`        | Identifier of the SBOM processing engine                     |
| `interlynk:sbom:org_id`                | Identifier of the organization generating SBOM               |
| `interlynk:sbom:signer_id`             | Identifier of the SBOM signer entity                         |
| `interlynk:sbom:export_type`           | Type of SBOM export used in generating the SBOM              |

## `interlynk:metadata`

| Property Name                              | Description                                            |
| ------------------------------------------ | ------------------------------------------------------ |
| `interlynk:metadata:product_id`            | Identifier of the underlying product                   |
| `interlynk:metadata:version_id`            | Identifier of the product version                      |
| `interlynk:metadata:sbom_id`               | Identifier of the SBOM associated with product version |
| `interlynk:metadata:parts`                 | List of product part-IDs                               |

## `interlynk:component`

| Property Name                      | Description                     |
| ---------------------------------- | --------------------------------|
| `interlynk:component:component_id` | Identifier of the component     |
| `interlynk:component:source`       | Source of the component         |
| `interlynk:component:source_id`    | Identifier of the source        |

## `interlynk:vulnerability`

| Property Name                     | Description                      |
| --------------------------------- | ---------------------------------|
| `interlynk:service:healthz`       | Service healthz endpoint         |


## `interlynk:vulnerability`

| Property Name                     | Description                      |
| --------------------------------- | -------------------------------- |
| `interlynk:vulnerability:fixed_version`  | Version containing the fix|
