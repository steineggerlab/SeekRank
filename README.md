# SeekRank
SeekRank is a pipeline that ranks homologous protein sequences based on a regressor trained on experimental measures.\
By training regressors to predict experimental measures with embeddings from protein Language Model,\
and by searching for homologous proteins in a metagenomic database,\
SeekRank can predict and rank any experimental measures user desires for homologous proteins in a metagenomic database.

### SeekRank.ipynb
Jupyter Notebook for searching homologous proteins with good predicted experimental measures from metagenomic database.\
It will train a regressor on protein Language Model embeddings and experimental measures,\
search for homologous proteins in a metagenomic database, and rank them based on the regressor.\
You can also use the Jupyter Notebook via Google Colab by the following link: https://seekrank.steineggerlab.com\
Please see the notebook for more details on training data and usage.

### Regressor_paper.ipynb
Jupyter Notebook used for producing results in the paper below.\
It might produce slightly different results shown in the paper due to the randomness in the training process\
and the difference in the database searched against the training sequences.\
`training_seqs.fasta` in the repository is the same as the one used in the paper, which will be automatically used in the Jupyter Notebook.\
If you want to use your own training sequences, please replace `training_seqs.fasta` with your own fasta file from the code.

It will produce two output files:
1. `esm1b_nonredundant.m8`: Nonredundant mmseqs2 output file for searching homologous proteins in the metagenomic database.
2. `target_prediction.tsv`: Predicted experimental measures for the homologous proteins in the metagenomic database based on three different regressors.\
The file format is as follows:
```
#Example
seq_id  KNeighborsRegressor SVR RandomForestRegressor
```

### Citation
Eom, Hyunuk, et al. "Discovery of Highly Active Kynureninases for Cancer Immunotherapy through Protein Language Model." bioRxiv (2024): 2024-01. doi: https://doi.org/10.1101/2024.01.16.575968
