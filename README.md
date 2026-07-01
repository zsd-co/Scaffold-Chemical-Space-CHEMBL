# Scaffold-Chemical-Space-CHEMBL
Function:
Query ChEMBL database, perform data cleaning, molecular aggregation, PAINS filtering, scaffold generation & parallel matching, scaffold scoring and result export.

- Python 3.8+


Key Dependencies
- `chembl_downloader`：Execute SQL queries against the ChEMBL database
- `rdkit`：Cheminformatics processing toolkit
- `pandas`, `numpy`, `tqdm`

Main File
- `chembl.py`：script

Usage Instructions
1. Edit the `SQL_QUERY` at the top of the script for custom filtering, or use the default query directly.
2. Run the full pipeline via command line:

bash
```
python chembl.py --out output_dir
```

Configuration Guidelines
- To adjust the scaffold matching similarity threshold, modify the `min_sim` argument in the `batch_search_skeletons_parallel` function call.
- Tune the `max_workers` parameter to optimize parallel computing performance.
- To update target scaffolds, append SMILES strings to the `skeleton_smiles_list` array.

- `chembl_downloader` requires accessible connection to the ChEMBL database. If direct database access is unavailable, export query results to a local CSV file first, then modify the script to load the local file and skip the database query step.
- database: chembl_36.db
