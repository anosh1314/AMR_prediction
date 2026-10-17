# AMR_prediction

The top-ranked features included genes associated with mobile genetic elements (toxin-antitoxin systems, prophage-associated genes) and a chloramphenicol resistance gene (cat), suggesting the model partly captures lineages and plasmid-carrying strains rather than direct ciprofloxacin resistance mechanisms. 
Future work would add sequence-variant data and control for population structure.

Model	                Accuracy	   Balanced accuracy	      ROC-AUC
Logistic regression    	0.922          	0.896	              0.949
Random forest	          0.943	          0.893              	0.968
Gradient boosting	      0.941	          0.900              	0.972

  Ciprofloxacin; 80/20 stratified split; 1,935 isolates, 5,993 genes after frequency filtering
