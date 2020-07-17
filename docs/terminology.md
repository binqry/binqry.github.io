# Terminology

This page explains the terminologies in this project.

## Index

**Index** is a data which contains multiple (often a number of) [item manifests](#item-manifest).

## Index Dataset

**Index Dataset** is a dataset which consists of one [index](#index) and multiple [items](#item) included in
the index.

## Index Server

**Index Server** is an HTTP server which serves [index dataset](#index-dataset).  
It responds with appropriate JSON content to incoming Get requests.

The default index server for `binq` is [https://binqry.github.io/index](https://binqry.github.io/index),
which contains static index dataset as GitHub Pages.

## Item

An **Item** means a stuff which can be installed by `binq`.

## Item Manifest

An **Item Manifest** is an [index](#index) data for an [item](#item) which contains following information:

- **URL Format** to download the item
- **Versions** available for download
- **Checksums** to verify downloaded items
- **Default Output File Names** of files in the item
