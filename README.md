# LSAGSL: a layer self-attention-based Graph Neural Network for Synthetic lethality in human cancers
 
LSAGSL focuses on studying the correlation between different extracted features and proposes a GNN algorithm based on a multi-layer self-attention mechanism. In the process of gene information aggregation, LSAGSL requires that the information source exhibits a strong association with both target genes.Furthermore, LSAGSL enhances the detection of hierarchical correlations within individual genes and the overall correlation between pairs of genes through the incorporation of a dual-layer attention mechanism within genes and a singular fused attention mechanism between gene pairs. This enables the extraction of crucial information pertaining to the correlation between gene pairs for the purpose of SL prediction.



## Dataset
* SL data:  32,561 SL gene pairs involving 9,516 genes are used as our SL labels.
* SynLethKG: knowledge graph consists of 54,012 nodes of 11 types and 2,231,921 edges of 24 types of relations.

## Evaluation schems

We use 5-fold cross-validation (CV) in the following three evaluation settings 

<img src="https://github.com/JieZheng-ShanghaiTech/PiLSL/blob/main/evaluation_schems.jpg" width=60%/>

| Evaluation schems  | Description
|------- |----------|
| [C1 ](data/C1/) | Dataset is split by gene pairs, where both genes of a pair in test set can be present in the train set.| 
| [C2 ](data/C2/) | Dataset is split by genes, where exactly one gene of a pair in test set is present in the train set.|
| [C3 ](data/C3/) | Dataset is split by genes, where both genes of a pair in test set are not used in train set.

## Requirements
```bash
pip install -r requirements.txt
```

## Running the code

```
python train.py 
    -d C1/cv_1           # evalution schem
    -e C1/cv_1           # the name for the log for experiments
    --gpu=0              # ID of GPU
    --hop=3              # size of the hops for enclosing grpah
    --batch=512          # batch size for samples
    --emb_dim=64         # size of embedding for GNN layers
    -b=10                # size of basis for relation kernel
    --l2=0.0001          # coefficient of regularizer
    -l=3                 # number of GCN layers
```


