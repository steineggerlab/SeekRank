# SeekRank
SeekRank is a pipeline that ranks homologous protein sequences based on a regressor trained on experimental measures.\
By training regressors to predict experimental measures with embeddings from protein Language Model,\
and by searching for homologous proteins in a metagenomic database,\
SeekRank can predict and rank any experimental measures user desires for homologous proteins in a metagenomic database.

## SeekRank.ipynb
Jupyter Notebook for searching homologous proteins with good predicted experimental measures from metagenomic database (Colabfold database).\
It will train a regressor on protein Language Model embeddings and experimental measures, search for homologous proteins in a metagenomic database, and rank them based on the regressor.\
You can also use the Jupyter Notebook via Google Colab by the following link: https://seekrank.steineggerlab.com

### How to run
- You need one fasta file containing protein sequences and experimental values for the sequences.\
    The fasta file should be in the following format:
    ```
    >seq_id_1 experimental_value_1
    protein_sequence_1
    >seq_id_2 experimental_value_2
    protein_sequence_2
    ...
    ```
    You can use the provided `training_seqs.fasta` in the repository as an example.
- Upload the training fasta file by running the first cell of the notebook.
- Choose options for training regressor.
- Run rest of the cells

### Output file
- top_ranked_target_list.tsv: Contains names, predicted experimental values, and sequences of the targets on each column respectively, sorted by predicted values.
    ```
    seq_id  predicted_experimental_value    protein_sequence
    A0A261TMR2  0.975792    MHTREACLQA...
    ```

## Regressor_paper.ipynb
Jupyter Notebook used for producing results in the paper below.\
It might produce slightly different results shown in the paper due to the randomness in the training process\
and the difference in the database searched against the training sequences (using Colabfold database currently, supposed to be BFD + Metaclust2).

### How to run
- On your machine:
    1. Git clone the repository.
    2. Open and run the Jupyter Notebook making sure you are working in the same directory as the notebook.
    ```
    git clone https://github.com/steineggerlab/SeekRank.git
    cd SeekRank
    # run Regressor_paper.ipynb
    ```

- On Google Colab:
    1. Open the notebook via the following link: https://github.com/steineggerlab/SeekRank/blob/main/Regressor_paper.ipynb
    2. Upload `training_seqs.fasta` in the repository or your own training data in the `/content`. If you are using your own training data, please change a directory in the notebook in the section `1.1 Preparing data for training`.
    3. Run the notebook.

### Output file:
- `target_prediction.tsv`: Predicted experimental measures for the homologous proteins in the metagenomic database based on three different regressors.\
    The file format is as follows:
    ```
    seq_id  KNeighborsRegressor SVR RandomForestRegressor   protein_sequence
    10034|scaffold453036_1|+110|01  47184.0 40469.28496161223   44026.08    MAAVGKP...
    ```

## Publications
Eom, Hyunuk, et al. "Discovery of highly active kynureninases for cancer immunotherapy through protein language model." Nucleic Acids Research 53.1 (2025), doi: https://doi.org/10.1093/nar/gkae1245
