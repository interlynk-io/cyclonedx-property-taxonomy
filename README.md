# Interlynk CycloneDX Property Taxonomy

This is the official listing of Interlynk's CycloneDX property namespace and taxonomy. The document lists all reserved properties, however the actual SBOM may use a subset of these depending on the product type and environment.

See [CycloneDX official documentation](https://github.com/CycloneDX/cyclonedx-property-taxonomy) for additional details.

## Naming convention

All Interlynk property names use `snake_case` for multi-word segments (e.g., `interlynk:build:optimization_level`). Namespace segments are lower-case.

## `interlynk`

| Namespace                 | Description                                              |
| --------------------------| -------------------------------------------------------- |
| `interlynk:sbom`          | SBOM document level properties                           |
| `interlynk:metadata`      | SBOM metadata level properties                           |
| `interlynk:component`     | Properties associated with a component                   |
| `interlynk:service`       | Properties associated with a service                     |
| `interlynk:vulnerability` | Properties associated with a vulnerability               |
| `interlynk:build`         | Build-time metadata affecting the shipped artifact       |
| `interlynk:linker`        | Post-link ground truth derived from the linker map       |
| `interlynk:hardware`      | Hardware device attributes (for HBOM components)         |


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

| Property Name                            | Description                     |
| -----------------------------------------| --------------------------------|
| `interlynk:component:component_id`       | Identifier of the component     |
| `interlynk:component:source`             | Source of the component         |
| `interlynk:component:source_id`          | Identifier of the source        |
| `interlynk:component:end_of_support_date`| Component end of support date   |
| `interlynk:component:support_level`      | Support level of component      |

## `interlynk:service`

| Property Name                     | Description                      |
| --------------------------------- | ---------------------------------|
| `interlynk:service:healthz`       | Service healthz endpoint         |


## `interlynk:vulnerability`

| Property Name                     | Description                      |
| --------------------------------- | -------------------------------- |
| `interlynk:vulnerability:fixed_version`  | Version containing the fix|

## `interlynk:build`

Build-time metadata that materially affects the shipped artifact's identity. Typically placed on a `firmware`, `application`, or `library` component.

| Property Name                           | Description                                                                    |
| ----------------------------------------| ------------------------------------------------------------------------------ |
| `interlynk:build:toolchain`             | Compiler/linker identifier (e.g., `IAR ICCARM/ILINK`, `GCC arm-none-eabi`)     |
| `interlynk:build:cpu`                   | Target CPU variant (e.g., `Cortex-M0+`, `Cortex-M4F`)                          |
| `interlynk:build:endian`                | Target byte order (`little` or `big`)                                          |
| `interlynk:build:optimization_level`    | Compiler optimization level (e.g., `None`, `Low`, `Medium`, `High-Size`)       |
| `interlynk:build:output_format`         | Output artifact format (`ELF`, `Intel HEX`, `Binary`, `Motorola S-record`)     |

## `interlynk:linker`

Post-link ground truth derived from a linker map file. Placed on `library` components representing auto-linked runtime archives, or on the primary firmware component.

| Property Name                        | Description                                                                       |
| -------------------------------------| --------------------------------------------------------------------------------- |
| `interlynk:linker:archive_name`      | Filename of a statically-linked archive (e.g., `dl6M_tln.a`). Decodes to architecture/endian/variant via toolchain-specific grammar |
| `interlynk:linker:dlib_abi_version`  | Runtime library ABI version from runtime-model attributes                         |
| `interlynk:linker:symbol_redirect`   | Linker symbol redirect (e.g., `_Printf=_PrintfLargeNoMb`). Multi-valued           |

## `interlynk:hardware`

Hardware device attributes for `device` components in an HBOM.

| Property Name                   | Description                                                          |
| --------------------------------| -------------------------------------------------------------------- |
| `interlynk:hardware:cpu`        | CPU/core variant of the device (e.g., `Cortex-M0+`, `Cortex-M4F`)    |
| `interlynk:hardware:fpu`        | Floating-point unit variant (e.g., `None`, `VFPv4-SP`)               |
| `interlynk:hardware:mcu_family` | MCU family identifier (e.g., `STM32L0`, `nRF52`)                     |
