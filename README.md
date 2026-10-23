# NutriEstimate

This repository contains the code used in the study:

Côté M, Hamadi W, Laramée C, Pomerleau S, Provencher V, Gagné C, Lamarche B. Estimating Nutrient       Composition of Packaged Foods Using Natural Language Processing and Optimization Modeling. Current Developments in Nutrition, 2026. https://doi.org/10.1016/j.cdnut.2026.109387

# Overview
Food composition databases are essential for dietary assessment and nutrition research, but they are often incomplete and primarily composed of generic foods.

This project introduces a pipeline combining Natural Language Processing (NLP) and optimization modeling to estimate the complete nutrient composition of packaged foods based on:

&emsp;-Nutrition Facts Tables (NFTs)

&emsp;-Ingredient lists

&emsp;-Canadian Nutrient File (CNF - 2026)

The approach allows the estimation of ingredient proportions and thus the generation of a complete nutrient profile for packaged foods.

# Methodology
The workflow consists of two main phases:

## Phase 1: Ingredient Matching Using FoodBERT
FoodBERT is used to generate embeddings for ingredients appearing on food labels and ingredients contained in the CNF.

Ingredient matches are identified using cosine similarity between embeddings.

## Phase 2: Optimization Modeling
An optimization model:

  &emsp;-identifies the best CNF match for each ingredient;
  &emsp;-estimates ingredient proportions (g/100 g);
  &emsp;-minimizes the error between estimated nutrients and known Nutrition Facts Table values.


The final output is:

  &emsp;-ingredient proportions by weight;
  &emsp;-estimated nutrient composition;

# Data Sources
The methodology was developed using:

  &emsp;--Canadian Nutrient File (CNF) 2015
  &emsp;--Food Quality Observatory (FQO) database
The original datasets are not included in this repository.


# Requirements

numpy
pandas
torch
transformers
tokenizers
huggingface_hub
spacy
scikit-learn
scipy
pyomo
tqdm
xlsxwriter
cvxopt

Install with:
pip install -r requirements.txt

Download the spacy language model:
python -m spacy download en_core_web_lg

The IPOPT solver is required to run the optimization model and must be installed separately.


# Citation
If you use this code, please cite:

@article{cote2026foodbert,
  title={Estimating Nutrient Composition of Packaged Foods Using Natural Language Processing and Optimization Modeling},
  author={Côté, Melina and Hamadi, Wiam and Laramée, Catherine and Pomerleau, Sonia and Provencher, Véronique and Gagné, Christian and Lamarche, Benoît},
  journal={Current Developments in Nutrition},
  year={2026},
  doi={10.1016/j.cdnut.2026.109387}
}

# License
This project is licensed under the GNU Affero General Public License v3.0 (AGPL-3.0).

You are free to use, modify, and distribute this software. Any derivative work must also be distributed under the same license and the corresponding source code must remain available. If this software is used as part of a network service (e.g., API, cloud platform, web application), the modified source code must also be made available under the AGPL-3.0 terms.

See the LICENSE file for details.

# Acknowledgements
This work was conducted at Université Laval in collaboration with the Centre Nutrition, santé et société (NUTRISS) and the Institut Intelligence et Données (IID). 【1-e456ac】

## References

If you use this code, please credit the creators of the underlying model:

* **FoodBERT Model & Paper:** 
  Chantal, M. P., et al. (2021). *Exploiting Food Embeddings for Ingredient Substitution*.(https://github.com/ChantalMP/Exploiting-Food-Embeddings-for-Ingredient-Substitution)

