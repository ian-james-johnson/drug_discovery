# Coronavirus Drug Discovery Project

---

# Table of Contents

---

- [Executive Summary](#executive-summary)
    - [Project Objectives](#project-objectives)
    - [Conclusions and Takeaways](#conclusions-and-takeaways)
    - [Next Steps and Recommendations](#next-steps-and-recommendations)    
- [Data Dictionary](#data-dictionary)
- [Initial Questions](#initial-questions)
- [Formal Hypotheses](#formal-hypotheses)
- [Pipeline Stages Breakdown](#pipeline-stages-breakdown)
    - [Plan](#plan)
    - [Acquire](#acquire)
    - [Prepare](#prepare)
    - [Explore](#explore)
    - [Model and Evaluate](#model-and-evaluate)
- [Conclusion and Next Steps](#conclusion-and-next-steps)
- [Reproduce My Project](#reproduce-my-project)

---

### Executive Summary

[(Back to top)](#table-of-contents)

- Developed a machine learning model that can predict if chemical compounds may be likely drug candidates for treating coronovirus.
- The machine learning model takes in data from ChEMBL.
- The Lipinski descriptors and the Pubchem fingerprints are calculated from the ChEMBL data.
- A decision tree is used to predict the pIC50 of chemical compounds for a coronavirus target.

---

#### Project Objectives

[(Back to top)](#table-of-contents)

- Find a target within coronavirus.
- Judge "drug-likeness" of chemical compounds using the Lipinski descriptors.
- Predict the pIC50 of chemical compounds for the coronavirus target by using the Pubchem fingerprints as the predictive variables.
- Construct a ML regression model that accurately predicts pIC50
- Complete end-to-end ML project encompassing all phases of DS pipeline
- Document code, process (data acquistion, preparation, exploratory data analysis and statistical testing, modeling, and model evaluation), findings, and key takeaways in a Jupyter Notebook report
- Create modules as necessary that make my process repeateable
- Include all work in github repo with README to provide high level overview and instructions for replication

#### Conclusions and Takeaways 

[(Back to top)](#table-of-contents)

- The machine learning model can predict the pIC50 of chemical compounds for a coronavirus target.
- The model performs better when there are many examples of both active and inactive chemical compounds.
- If other targets are chosen, then care should be taken such the "None" and similar values are removed from numeric featurs. String values will break calculations on numeric features.

#### Next Steps and Recommendations

[(Back to top)](#table-of-contents)

- Improve the predictive accuracy of the model
- Make the notebook so that a non-coder can give any disease and target for analysis when prompted

#### Audience
- Anyone interested in taking a look at my project

#### Project Context
- The full dataset come from ChEMBL
- This database contains biochemical information about a vast array of diseases, disease target, and chemical compounds that were tested with the diseases.

#### Data Dictionary

[(Back to top)](#table-of-contents)

---

| Word | Definition | 
| ----- | ----- | 
| standard_value | A standardized value derived from Ki and IC50 in the literature |
| canonical_smiles | A string variable that represents a chemical structure |
| molecule_chembl_id | A unique ID for a chemical compound in ChEMBL |
| MW| Molecular weight (daltons) |
| LogP | Ratio of solubility in fat to solubility in water |
| NumHDonors | The number of hydrogen donors that a chemical compound has |
| NumHAcceptors | The number of hydrogen acceptors that a chemical compound has|
| Lipinski Descriptors | The "Rule of Five" that describes the drug-likeness of a chemical compound |
| fingerprints | A dataframe where each column is a boolean question describing the chemical compounds |
| IC50 | Half the concentration of a chemical compounded needed to reach maximum inhibition of the target |

---

#### Initial Questions

[(Back to top)](#table-of-contents)

- Do the active and inactive compounds have different values for the Lipinski descriptors?
- Do the active and inactive compounds have different values for the Pubchem fingerprints?

#### Formal Hypotheses

[(Back to top)](#table-of-contents)

- See notebook for formal hypotheses and statistical testing

---

### Pipeline Stages Breakdown

---

##### Plan

[(Back to top)](#table-of-contents)

- [x] Create README.md with data dictionary, project and business goals, and come up with initial hypotheses.
- [x] Acquire data from ChEMBL.
- [x] Clean and prepare data. Create a function to automate the process, store the function in a prepare.py module, and prepare data in Final Report Notebook by importing and using the function.
- [x] Clearly define at least two hypotheses, set an alpha, run the statistical tests needed, reject or fail to reject the Null Hypothesis, and document findings and takeaways.
- [x] Establish a baseline accuracy and document well.
- [x] Train several different regression models.
- [x] Evaluate models on train and validate datasets.
- [x] Choose the model with that performs the best and evaluate that single model on the test dataset.
- [x] Document conclusions, takeaways, and next steps in the Final Report Notebook.
- [x] Iterate back through the pipeline imporving each phase as time permits
___

##### Acquire

[(Back to top)](#table-of-contents)

- Store functions that are needed to acquire data from ChEMBL; make sure the acquire.py module contains the necessary imports to run my code.
- The final function will return a pandas DataFrame.
- Import the acquire function from the acquire.py module and use it to acquire the data in the Final Report Notebook.
- Complete some initial data summarization (`.info()`, `.describe()`, `.shape()`, ...).
___

##### Prepare

[(Back to top)](#table-of-contents)

- Store functions needed to prepare the data; make sure the module contains the necessary imports to run the code. The final function should do the following:
    - Split the data into train/validate/test.
    - Handle any missing values.
    - Handle erroneous data and/or outliers that need addressing.
    - Encode variables as needed.
    - Identify unit measures and decide how to best scale any numeric data
    - Remove outliers
- Import the prepare function from the prepare.py module and use it to prepare the data in the Final Report Notebook.
- Plot distributions of individual variables.
___

##### Explore

[(Back to top)](#table-of-contents)

- Answer key questions, my hypotheses, and figure out the features that can be used in a regression model to best predict the target variable. 
- Run statistical tests in data exploration. Document my hypotheses, set an alpha before running the tests, and document the findings well.
- Create visualizations and run statistical tests that work toward discovering variable relationships (independent with independent and independent with dependent). 
- Summarize my conclusions, provide clear answers to my specific questions, and summarize any takeaways/action plan from the work above.
___

##### Model and Evaluate

[(Back to top)](#table-of-contents)


- Train (fit, transform, evaluate) models.
- Feature Selection (after initial iteration through pipeline): Are there any variables that seem to provide limited to no additional information? If so, remove them.
- Test the final model on the out-of-sample data (the testing dataset), summarize the performance, interpret and document the results.

---

### Conclusion and Next Steps

[(See Executive Summary)](#executive-summary)
The model described herein can predict the IC50 of chemical compounds for coronavirus target; which can be used to pre-screen drug-candidates before expensive, time-consuming, and risky lab experiments.
---

### Reproduce My Project
---
[(Back to top)](#table-of-contents)

Copy the coronavirus_drug_discovery.ipynb file. If you don't have the ChEMBL client, rdkit, and padelpy installed; then un-comment (remove # sign) from lines that contain installation commands. The code for installing the libraries are in the same cell as the library imports. Finally, run the notebook.
 

