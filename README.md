# AMR_prediction
# Predicting Ciprofloxacin Resistance in E. coli from Gene Content

## Question
Can the presence or absence of accessory genes predict whether an *E. coli* isolate is resistant to ciprofloxacin?

## Data
Public dataset from Moradigaravand et al. (2018), "Prediction of antibiotic resistance in *Escherichia coli* from large-scale pan-genome data," PLoS Computational Biology 14(12): e1006258 (github.com/DaneshMoradigaravand/PanPred). This project is a simplified, independent exercise using that data, not a reproduction of the paper's full analysis.

- `AccessoryGene.csv`: gene presence/absence (1/0) per isolate
- `Metadata.csv`: resistant (R) / susceptible (S) phenotypes per antibiotic

## Method
- Kept isolates with a ciprofloxacin result: 1,935 isolates (429 resistant, 1,506 susceptible)
- Removed genes present in more than 99% or fewer than 1% of isolates: 5,993 genes remained
- 80/20 stratified train/test split (random seed 42)
- Compared logistic regression, random forest, and gradient boosting (scikit-learn)

## Results (held-out 20%)

| Model | Accuracy | Balanced accuracy | ROC-AUC |
|---|---|---|---|
| Logistic regression | 0.922 | 0.896 | 0.949 |
| Random forest | 0.943 | 0.893 | 0.968 |
| Gradient boosting | 0.941 | 0.900 | 0.972 |


## Feature importance
The top random forest features included genes that appear to be linked to mobile genetic elements (e.g., toxin-antitoxin genes `pemI` and `chpS`), prophage-associated genes, and the chloramphenicol resistance gene `cat`. This suggests the model partly captures lineages and plasmid-carrying strains rather than direct ciprofloxacin resistance mechanisms. I did not test this explanation.

## Limitations
- One antibiotic only
- Single train/test split; no hyperparameter tuning
- Closely related isolates may appear in both train and test sets, which can inflate performance
- Gene presence/absence cannot capture point mutations, which drive most ciprofloxacin resistance

## Future work
Add sequence-variant data, control for population structure (e.g., split by lineage), and extend to other antibiotics.
