# Operation Manual

Function:
Query ChEMBL database, perform data cleaning, molecular aggregation, PAINS filtering, scaffold generation & parallel matching, scaffold scoring and result export.

- Python 3.8+

Main File
- `Skeleton_Hit_Performance_Score.py`：script
- `chemical_space_analysis.py`：script
- `export_approved_drugs.py`：script

Usage Instructions
1. Edit the `SQL_QUERY` at the top of the script for custom filtering, or use the default query directly.

2. To update target scaffolds, open `Skeleton_Hit_Performance_Score.py` and append SMILES strings to the `skeleton_smiles_list` array.

3. To use your downloaded ChEMBL SQLite database directly, open `export_approved_drugs.py` and modify the `chembl_db_path` variable.

4. To use your own data folder, open `chemical_space_analysis.py` and modify the `base_dir` variable in section `2. Path settings`.

5. Run the full pipeline via command line:

bash
# Obtain the compound dataset of scaffold hits
```
python chembl.py --out output_dir
```

# Obtain the approved drug dataset
```
python export_approved_drugs.py
```

# Complete the chemical space analysis
```
python chemical_space_analysis.py
```




Configuration Guidelines
- To adjust the scaffold matching similarity threshold, modify the `min_sim` argument in the `batch_search_skeletons_parallel` function call.
- Tune the `max_workers` parameter to optimize parallel computing performance.

- `chembl_downloader` requires accessible connection to the ChEMBL database. If direct database access is unavailable, export query results to a local CSV file first, then modify the script to load the local file and skip the database query step.
