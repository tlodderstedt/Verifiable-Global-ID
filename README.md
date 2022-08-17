# Verifiable-Global-ID

Table of contents
- [Verifiable-Global-ID](#verifiable-global-id)
	- [Introduction](#introduction)
	- [Folder structure](#folder-structure)
	- [Converting JSON Schema to human-readable format](#converting-json-schema-to-human-readable-format)
	- [Build the HTML](#build-the-html)
	- [References](#references)

## Introduction

Specification for a global identity credential.

## Folder structure

In the repository, we have one main folder `schemas` where we store all JSON schemas.
Global Verifiable ID schema is extensible, hence every JSON schema lives in its
directory. The `schemas/core` directory is reserved for the core JSON schema. Other
schemas must extend the JSON schema.

In every schema folder you can find

- A `README.md`, which describes the schema and links to relevant documentation.
- A versioned folder `YYYY-MM(_VV)`, e.g., `2022-08`. Year and month mark the stable version publication date and are mandatory, version number is optional `VV` and should be added if several versions are published within the same month.
- In every versioned folder `YYYY-MM(_VV)` we store
  - `schema.json` which is the main schema
  - `examples` folder that contains one or more valid examples
  - optional `html` folder that contains human-readable JSON schema representation in HTML format (see section [Convert JSON Schema to human-readable format])
  - optional `definitions` folder that contains one or more JSON schemas that are referenced in the main `schema.json`

## Converting JSON Schema to human-readable format

We are using [JSON Schema for humans](https://github.com/coveooss/json-schema-for-humans) to convert schemas into a human-readable HTML format.

After installing the schema doc generator, run

```bash
generate-schema-doc --minify --no-link-to-reused-ref schema.json html/
```

A successful conversion will result in a `html/schema_doc.html` file.

## Build the HTML

```docker run -v `pwd`:/data danielfett/markdown2rfc main.md```

## References

- [JSON Schema for humans](https://github.com/coveooss/json-schema-for-humans)