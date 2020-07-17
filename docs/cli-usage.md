# CLI Usage of **binq**

This page describes various usages of [**binq**](https://github.com/binqry/binq/) command.

## General Usage

Syntax:

```sh
binq [install] [arguments...] [options...]
binq COMMAND [arguments...] [options...]
binq -h|--help  # Show general help
```

Subcommands:

```sh
binq install       # (Default command) Install binary or archive item
binq index         # List Items on Index Server
binq new           # Create Item Manifest
binq revise        # Add/Edit/Delete a version in Item Manifest
binq verify        # Verify checksum of a version in Item Manifest
binq register      # Register/Update Item onto Local Index
binq modify        # Modify Item properties on Local Index
binq deregister    # Deregister Item from Local Index
binq self-upgrade  # Upgrade binq binary itself
binq version       # Show binq version
```

Run `binq COMMAND -h|--help` to see reference of each subcommand.

General Options:

```sh
-h|--help                # Show help
-L, --log-level string   # Log level (debug,info,notice,warn,error)
```

## Install "Items"

An [item](../terminology/#item) means a stuff which can be installed by `binq`.

See [Quickstart](../quickstart/) for this use case.

## Self Upgrade

`binq self-upgrade` is command to upgrade the executing binary itself when newer version is
available.

It uses the functionality of `binq` itself.  
It has a few command options but you will rarely need to specify either of them.

## List Items on "Index Server"

[Index Server](../terminology/#index-server) serves dataset of multiple items.

`binq index` is command to list items on an index server.

Syntax:

```sh
binq index [-s|--server SERVER] [-o|--output FORMAT] [GENERAL_OPTIONS]
```

If you omit `-s|--server` option, [https://binqry.github.io/index](https://binqry.github.io/index)
will be queried as default server.

You can specify `text` or `json` as `-o|--output` option. Default is `text`.

## Create and Edit "Item Manifests"

An [item manifest](../terminology/#item-manifest) is data which describes how to install the item.

`binq` has several subcommands to create and edit item manifest files in the form of JSON.

### Create a Manifest

`binq new` is command to create an item manifest.

Syntax:

```sh
binq new URL_FORMAT [-v|--version VERSION] [-f|--file OUTPUT_FILE] \
  [-r|--replace REPLACEMENTS] [-e|--ext EXTENSIONS] \
  [-R|--rename RENAME_FILES] [GENERAL_OPTIONS]
```

### Revise a version in a Manifest

`binq revise` is command to add/edit/delete a version for the manifest.

Syntax:

```sh
# Add or Update Version in the Manifest
binq revise MANIFEST_FILE [-v|--version] VERSION \
  [-s|--sum CHECKSUMS] [-u|--url URL_FORMAT] \
  [-r|--replace REPLACEMENTS] [-e|--ext EXTENSIONS] \
  [-R|--rename RENAME_FILES] [--latest] [--no-latest] [-y|--yes] \
  [GENERAL_OPTIONS]

# Delete Version in the Manifest
binq revise MANIFEST_FILE VERSION --delete [-y|--yes] [GENERAL_OPTIONS]
```

In most cases, you won't need such options like `--url`, `--replace` and `--rename` because they
rarely differs between versions.

If the checksums of items are ambiguous, you can use following `binq verify` command.

### Verify a version in a Manifest

`binq verify` is command to verify the checksum of a version of an item.  
It can also be used to generate SHA-256 checksum for the version.

```sh
# Download a Version in the Manifest and Verify its checksum
binq verify MANIFEST_FILE [-v|--version VERSION] [--os OS] \
  [-a|--arch ARCH] [-y|--yes] [--keep] [GENERAL_OPTIONS]
```

## Manipulate "Index Dataset" in Local File System

[Index Dataset](../terminology/#index-dataset) is a dataset which holds multiple item manifests.

`binq` has several subcommands to create and edit index dataset in local file system.

### Register or Update an Item on Index

`binq register` is command to register or update an item manifest onto index dataset which is
located in a directory.

Syntax:

```sh
binq register pato/to/root[/index.json] MANIFEST_FILE \
  [-n|--name NAME] [-p|--path PATH] [-y|--yes] [GENERAL_OPTIONS]
```

The name of [index](../terminology/#index) data file must be `index.json`.  
When `index.json` does not exist, it will be created.

If you want to change the name or path of a registered item, use following `binq modify` command.

### Modify an Item Info on Index

`binq modify` is command to edit the properties of an item on index dataset.

Syntax:

```sh
binq modify pato/to/root[/index.json] NAME \
  [-n|--name NEW_NAME] [-p|--path PATH] [-y|--yes] [GENERAL_OPTIONS]
```

This command has no functionality to edit the manifest itself.  
You should use `binq revise` or `binq verify` command for the purpose.

### Deregister an Item from Index

`binq deregister` is command to remove an item from index dataset.

Syntax:

```sh
binq deregister pato/to/root[/index.json] NAME [-y|--yes] \
  [GENERAL_OPTIONS]
```
