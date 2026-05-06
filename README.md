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
| `interlynk:oss_index`     | OSS-index enrichment and version inference metadata       |
| `interlynk:oss_index_db`  | Local OSS-index database manifest metadata               |


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

Post-link ground truth derived from a linker map file. Placed on `library` components representing auto-linked runtime archives, linker-attributed source/object components, excluded components, or on the primary firmware component.

| Property Name                                | Description                                                                                           |
| ---------------------------------------------| ----------------------------------------------------------------------------------------------------- |
| `interlynk:linker:archive_name`              | Filename of a statically-linked archive (e.g., `dl6M_tln.a`). Decodes to architecture/endian/variant via toolchain-specific grammar |
| `interlynk:linker:archive_path`              | Path to the statically-linked archive as reported or resolved from linker evidence                    |
| `interlynk:linker:archive_member`            | Object/member name within a statically-linked archive                                                 |
| `interlynk:linker:dlib_abi_version`          | Runtime library ABI version from runtime-model attributes                                             |
| `interlynk:linker:exclusion_evidence`        | Linker-derived evidence explaining why a candidate component was excluded from the linked artifact    |
| `interlynk:linker:exclusion_reason`          | Machine-readable reason a candidate component was excluded from the linked artifact                   |
| `interlynk:linker:map_file`                  | Linker map file path or identifier used as post-link evidence                                         |
| `interlynk:linker:requestor`                 | Component, object, or symbol that caused the linker to include another object or library              |
| `interlynk:linker:runtime_archive_match`     | Runtime archive match evidence used to attribute linked runtime libraries                             |
| `interlynk:linker:symbol`                    | Symbol name observed in linker evidence                                                               |
| `interlynk:linker:symbol_redirect`           | Linker symbol redirect (e.g., `_Printf=_PrintfLargeNoMb`). Multi-valued                               |

## `interlynk:hardware`

Hardware device attributes for `device` components in an HBOM.

| Property Name                   | Description                                                          |
| --------------------------------| -------------------------------------------------------------------- |
| `interlynk:hardware:cpu`        | CPU/core variant of the device (e.g., `Cortex-M0+`, `Cortex-M4F`)    |
| `interlynk:hardware:fpu`        | Floating-point unit variant (e.g., `None`, `VFPv4-SP`)               |
| `interlynk:hardware:mcu_family` | MCU family identifier (e.g., `STM32L0`, `nRF52`)                     |

## `interlynk:oss_index_db`

Metadata describing the local OSS-index database used during source and package attribution. Typically placed on SBOM metadata.

| Property Name                                  | Description                                      |
| -----------------------------------------------| ------------------------------------------------ |
| `interlynk:oss_index_db:built_at`              | Build timestamp for the OSS-index database       |
| `interlynk:oss_index_db:db_key`                | Database key or identifier                       |
| `interlynk:oss_index_db:format_version`        | OSS-index database manifest format version       |
| `interlynk:oss_index_db:sha256`                | SHA-256 digest of the OSS-index database         |
| `interlynk:oss_index_db:size_compressed`       | Compressed database size in bytes                |
| `interlynk:oss_index_db:size_uncompressed`     | Uncompressed database size in bytes              |

## `cdx`

CycloneDX property names emitted when using common CycloneDX ecosystem conventions outside the Interlynk namespace.

| Property Name           | Description                                              |
| ------------------------| -------------------------------------------------------- |
| `cdx:device:function`   | Function or role assigned to a device component          |
| `cdx:reproducible`     | Indicates whether the generated SBOM is reproducible     |

## `lynkctl`

Tool-specific properties emitted by `lynkctl` to preserve scanner, resolver, and repository attribution details.

| Property Name                       | Description                                                                 |
| ------------------------------------| --------------------------------------------------------------------------- |
| `lynkctl:confidence`                | Confidence score or level for a component attribution                       |
| `lynkctl:install_method`             | Installation or discovery method associated with the component              |
| `lynkctl:link_type`                  | Linkage type associated with the component                                  |
| `lynkctl:nearest_version`            | Nearest version inferred from repository or tag evidence                    |
| `lynkctl:raw_name`                   | Raw component name before normalization                                     |
| `lynkctl:submodule:commit`          | Git submodule commit associated with the component                          |
| `lynkctl:submodule:path`            | Git submodule path associated with the component                            |
| `lynkctl:submodule:url`             | Git submodule URL associated with the component                             |
| `lynkctl:vendored_in:<project>`     | Dynamic property indicating that a component was found vendored in project  |
| `lynkctl:version_status`            | Status explaining whether an inferred version is exact, approximate, or missing |

## `interlynk:oss_index`

Properties emitted from OSS-index enrichment and version inference.

| Property Name                              | Description                                             |
| -------------------------------------------| ------------------------------------------------------- |
| `interlynk:oss_index:indexed_range`                  | Indexed version range associated with a matched project |
| `interlynk:oss_index:version_candidates`             | Candidate versions found by OSS-index attribution       |
| `interlynk:oss_index:version_indexed_range`          | Indexed version range used during version inference     |
| `interlynk:oss_index:version_method`                 | Method used to infer or select a component version      |
