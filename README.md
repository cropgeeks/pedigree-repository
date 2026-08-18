# Plant Pedigree Repository

This is a repository of publicly available plant pedigree datasets.

The datasets are first grouped by crop and then per publication/reference:

```
Repository
│   README.md
│
└───strawberry
│   └───publication_reference_1
|   |   |   LICENSE
|   │   │   README.md
|   │   │   CITATION.cff
|   │   │   index.json
|   │   │   full-pedigree.helium
|   |   |   uk-pedigree.helium
|   │   │   trait-data.helium
|   │   └─────────────────────
|   |
│   └───publication_reference_2
|       |   LICENSE
|       │   README.md
|       │   CITATION.cff
|       │   index.json
|       │   pedigree.helium
|       │   trait-data.helium
|       └─────────────────────
│
└───barley
│   └───publication_reference_1
│       │ ...
⋮        ⋮
```

Each publication/reference-level folder will contain:

- A `README.md` file with a short explanation of the dataset.
- A `LICENSE` file detailing the access permissions to the data in the folder.
- An `index.json` file that contains information about the individual files within this folder (format below)
- Potentially a `CITATION.cff` file with detailed attribution/citation information in addition to any information provided in the readme or license.
- At least one pedigree file in [Helium](https://helium.hutton.ac.uk) format.
- Potentially one or multiple trait data files in Helium format.

## Index JSON file

Each dataset folder should contain a single `index.json` file of the following format:

| Field | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `title` | `string` | Yes | Human-readable title of this study. |
| `description` | `string` | No | Human-readable description of this study. |
| `createdOn` | `string` | Yes | ISO 8601 date or UTC timestamp of creation. |
| `createdOn` | `string` | No | URL to an external resource (e.g. a database or website). |
| `data` | `array[entry]` | Yes | List of data resources available for this study. |
| `data.title` | `string` | Yes | Human-readable title of the dataset. |
| `data.description` | `string` | No | Human-readable coverage scope of the dataset. |
| `data.files.pedigree` | `string` | Yes | Path to the `.helium`/`.txt` pedigree file. |
| `data.files.traits` | `array[string]` | No | List of `.helium`/`.txt` trait dataset files associated with the pedigree. |
| `data.files.image` | `string` | No | An image file that can be used by client applications as a banner for this dataset. |
| `data.createdOn` | `string` | Yes | ISO 8601 date or UTC timestamp of creation. |

Here is an example:

```json
{
  "title": "Barley pedigree from study XYY937592u",
  "description": "",
  "createdOn": "2026-08-17",
  "externalLink": "https://github.com/cropgeeks/pedigree-repository/tree/main/barley/test",
  "data": [
    {
      "title": "Global pedigree dataset",
      "description": "Global barley pedigree",
      "files": {
        "pedigree": "full-pedigree.helium",
        "traits": ["trait-data.helium"],
        "image": "banner.jpg"
      },
      "createdOn": "2026-08-17"
    },
    {
      "title": "UK pedigree dataset",
      "description": "Subset of the pedigree restricted to UK breeders",
      "files": {
        "pedigree": "uk-pedigree.helium",
        "traits": ["trait-data.helium"],
        "image": "banner.jpg"
      },
      "createdOn": "2026-09-12T09:12:37Z"
    }
  ]
}
```

In this example, we have a study containing barley pedigree data created in August 2026. The external URL just links to the repository itself, but could link to a database or website. There are we have two pedigree datasets within this folder. The first set is a pedigree file that contains the whole global pedigree. It's associated with a single trait data file. The second dataset contains a subset of the global pedigree restricted to UK breeders. The same trait data file is associated with this pedigree.

The `pedigree` and `traits` files can have arbitraty names, but the `index.json` file has to have this exact name per folder.

# License

The Apache License Version 2.0 applies to the entire repo except for subfolders that have their own license file. In such cases, the license file in the subfolder takes precedence.