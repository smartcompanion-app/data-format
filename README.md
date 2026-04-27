# SmartCompanion Data Format

This repository holds a specification of the data format for SmartCompanion apps. In addition examples are provided to demonstrate app features. The specification is defined within the provided JSON schema files. The JSON schema specifications are versioned.

## Versioning

The schema is versioned with a `major.minor` version. The minor version is increased for additive changes, so data files complying with current schema are compatible with the minor version increase. The major version is increased for breaking changes, i.e., data which is compliant to current schema will not comply to the schema after the major version increase.

### Versions

| Version | Description | JSON schema |
| --- | --- | --- |
| v1.0 | Defines the initial schema with the core data attributes `stations`, `tours`, `assets`, `languages`, `texts` and the `checksum`. In addtion the optional attributes `pins` and `servers` are defined. | https://smartcompanion-app.github.io/data-format/v1.0/schema.json |
| v1.1 | Defines the `share` attribute to provide a URL to share the app with friends. | https://smartcompanion-app.github.io/data-format/v1.1/schema.json |

## Examples

There are examples provided for the latest available JSON schema version:

 - [AI-generated multilanguage tour of animal stations](https://smartcompanion-app.github.io/data-format/animals/data.json)
 - [German language audiotour through the town "Bruck an der Großglocknerstraße"](https://smartcompanion-app.github.io/data-format/leon/data.json) © by Leon Schwaiger

## Specification

A human-readable documentation of the latest version of the JSON Schema can be found [here](https://smartcompanion-app.github.io/data-format).

## Inspiration

 - [XMLGuide](https://dl.acm.org/doi/abs/10.1145/1967486.1967549)
 - [TourML](https://github.com/IMAmuseum/tourml)
