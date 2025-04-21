# Plant Pedigree Repository

This is a repository of publicly available plant pedigree datasets.

The datasets are first grouped by crop and then per publication:

```
Repository
│   README.md
│
└───strawberry
│   └───publication1
|   |   |   LICENSE
│   │   │   README.md
│   │   │   pedigree.helium
│   │   │   trait-data.helium
│   │   └─────────────────────
│   └───publication2
|       |   LICENSE
│       │   README.md
│       │   pedigree.helium
│       │   trait-data.helium
│       └─────────────────────
│
└───barley
│   └───publication1
│       │ ...
⋮        ⋮
```

Each publication-level folder will contain:

- A `README.md` file with a short explanation of the dataset.
- A `LICENSE` file detailing the access permissions to the data in the folder.
- Potentially a `CITATION.cff` file with detailed attribution/citation information in addition to any information provided in the readme or license.
- A pedigree file in [Helium](https://helium.hutton.ac.uk) format.
- Potentially one or multiple trait data files.


# License

The Apache License Version 2.0 applies to the entire repo except for subfolders that have their own license file. In such cases, the license file in the subfolder takes precedence.