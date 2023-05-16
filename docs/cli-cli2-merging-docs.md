---
id: cli-cli2-merging
title: Migrating Old CLI To New CLI
---

# Migrating From Old CLI To New CLI
### Overview
This document contains cli commands that were migrated from the old cli, which is `morphir-elm`, into the new  all cli commands supported by the old cli,  and the **current** cli, `morphir`.


| Command           | Flags                                                     | Description                                                                    | Old CLI  | New CLI  |       New Command        | Comment                                            |
|-------------------|-----------------------------------------------------------|--------------------------------------------------------------------------------|:--------:|:--------:|:------------------------:|----------------------------------------------------|
| `make`            |                                                           |                                                                                | &#9989;  | &#9989;  |      `morphir make`      |                                                    |
|                   | -p , --project-dir  `<path>`                              | Root directory of the project where morphir.json is located.                   |          |          |                          |                                                    |
|                   | -o , --output `<path>`                                    | Target file location where the Morphir IR will be saved.                       |          |          |                          |                                                    |
|                   | -t, --types-only                                          | Only include type information in the IR, no values.                            |          |          |                          |                                                    |
|                   | -f, --fallback-cli                                        | Use old cli make function.                                                     |          |          |                          |                                                    |  
| `test`            |                                                           |                                                                                | &#9989;  | &#10008; |      `morphir test`      |                                                    |
|                   | -p, --project-dir `<path>`                                | Root directory of the project where morphir.json is located.                   |          |          |                          |                                                    |
| `stats`           |                                                           |                                                                                | &#10008; | &#9989;  |     `morphir stats`      |                                                    |
|                   | -i, --input `<path>`                                      | Source location where the Morphir IR will be loaded from.                      |          |          |                          |                                                    |
|                   | -o, --output `<path>`                                     | Target location where the generated code will be saved.                        |          |          |                          |                                                    |
| `dockerize`       |                                                           |                                                                                | &#10008; | &#9989;  |   `morphir dockerize`    |                                                    |
|                   | -p, --project-dir `<path>`                                | Root directory of the project where morphir.json is located                    |          |          |                          |                                                    |
|                   | -f, --force                                               | Overwrite any Dockerfile in target location                                    |          |          |                          |
| `gen`             |                                                           |                                                                                | &#9989;  | &#10008; |                          |                                                    |
|                   | -i, --input `<path>`                                      | Source location where the Morphir IR will be loaded from.                      |          |          |                          |                                                    |
|                   | -o, --output `<path>`                                     | Target location where the generated code will be saved.                        |          |          |                          |                                                    |
|                   | -t, --target `<type>`                                     | Language to Generate (Scala &#124; Cadl &#124; JsonSchema  &#124; TypeScript). |          |          |                          | To generate Scala, use command `morphir scala-gen` |
|                   | -e, --target-version `<version>`                          | Language version to Generate.                                                  |          |          |                          |                                                    |
|                   | -c, --copy-deps                                           | Copy the dependencies used by the generated code to the output path            |          |          |                          |                                                    |
|                   | -m, --modules-to-include `<comma.separated>`              | Limit the set of modules that will be included                                 |          |          |                          |                                                    |
|                   | -s, --include-codecs                                      | Generate JSON codecs                                                           |          |          |                          |                                                    |
|                   | -f, --filename `<filename>`                               | Filename of the generated JSON Schema                                          |          |          |                          |                                                    |
|                   | -cc, --custom-config `<filepath>`                         | A filepath to load additional configuration for the backend                    |          |          |                          |                                                    |
| `scala-gen`       |                                                           |                                                                                | &#10008; | &#9989;  |   `morphir scala gen`    |                                                    |
|                   | -i, --input `<path>`                                      | Source location where the Morphir IR will be loaded from                       |          |          |                          |                                                    |
|                   | -o, --output `<path>`                                     | Target location where the generated code will be saved                         |          |          |                          |                                                    |
|                   | <span style={{color: 'red'}}> -t, --target `<type>` </span> | Language to Generate                                                           |          |          |                          | <span style={{color:'red'}}>Deprecated</span>      |
|                   | -e, --target-version `<version>`                          | Language version to Generate                                                   |          |          |                          |                                                    |
|                   | -c, --copy-deps                                           | Copy the dependencies used by the generated code to the output path            |          |          |                          |                                                    |
|                   | -s, --include-codecs `<boolean>`                          | Generate the scala codecs as well                                              |          |          |                          |                                                    |
|                   | -m, --limitToModules  `<comma.separated>`                 | Limit the set of modules that will be included                                 |          |          |                          |                                                    |
| `json-schema-gen` |                                                           |                                                                                | &#10008; | &#9989;  | `morphir jsonschema gen` |                                                    |
|                   | -i, --input `<path>`                                      | Source location where the Morphir IR will be loaded from                       |          |          |                          |                                                    |
|                   | -o, --output `<path>`                                     | Target location where the generated code will be saved                         |          |          |                          |                                                    |
|                   | <span style={{color: 'red'}}> -t, --target `<type>` </span>    | Language to Generate                                                           |          |          |                          | <span style={{color:'red'}}>Deprecated</span>      |
|                   | -e, --target\-version `<version>`                         | Language version to Generate                                                   |          |          |                          |                                                    |
|                   | -f, --filename `<filename>`                               | Filename of the generated JSON Schema                                          |          |          |                          |                                                    |
|                   | -m, --limit-to-modules `<comma.separated>`                | Limit the set of modules that will be included                                 |          |          |                          |                                                    |
|                   | -g, --group-schema-by `<string>`                          | Group generate schema by package, module or type                               |          |          |                          |                                                    |
|                   | -c, --use-config                                          | Use configuration specified in the config file                                 |          |          |                          |                                                    |
|                   | -ls, --include `<comma.separated,list.of,strings>`        | Limit what will be included                                                    |          |          |                          |                                                    |
| `develop`         |                                                           |                                                                                | &#9989;  | &#10008; |    `morphir develop`     |                                                    |                                                |
|                   | -p, --port `<port>`                                       | Port to bind the web server to                                                 |          |          |                          |                                                    |
|                   | -o, --host `<host>`                                       | Host to bind the web server to.                                                |          |          |                          |                                                    |