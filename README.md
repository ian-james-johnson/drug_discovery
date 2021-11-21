# Coronavirus Drug Discovery Project

---

<img src="https://s19538.pcdn.co/wp-content/uploads/2018/08/Car-Gurus-Logo.jpg" alt="Car Gurus" title="Car Gurus Logo" width="600" height="300" />

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

| Feature                        | Description                                                                                                            | Data Type | Notes |
| ------------------------------ | ---------------------------------------------------------------------------------------------------------------------- | --------- | ------------- |
| `back_legroom`                  |  Legroom in the rear seat (inches)                                                          |   float     |   Used in model    |
| `city_fuel_economy`                  |  Gas mileage in city (mpg)                                                        |   float     |   Used in model    |
| `engine_displacement`                  |  measure of the cylinder volume of engine (cubic centimeters)                                                       |   float     |   Used in model    |
| `fuel_tank_volume`                  |  Volume of fuel tank (gallons)                                                          |   float     |   Used in model    |
| `height`                  |  Height of vehicle (inches)                                                        |   float     |   Used in model    |
| `highway_fuel_economy`                  |  Gas mileage in highway (mpg)                                                       |   float     |   Used in model    |
| `horsepower`                  |  Measure of engine power                                                          |   float     |   Used in model    |
| `length`                  |  Length of vehicle (inches)                                                         |   float     |   Used in model    |
| `maximum_seating`                  |  Total number of seats                                                         |   float     |   Used in model    |
| `mileage`                  |  Mileage of vehicle (miles)                                                          |   float     |   Used in model    |
| `wheelbase`                  |  Distance between centers of front and rear wheels (inches)                                                         |   float     |   Used in model    |
| `width`                  |  Width of vehicle (inches)                                                        |   float     |   Used in model    |
| `year`                  |  Year car was released                                                         |   int     |   Used in model    |


---
| Target | Definition | Data Type | Notes |
| ----- | ----- | ----- | ----- |
| `price` | Sales price of used car | float | Value being predicted |

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

- Establish a baseline accuracy to determine if having a model is better than no model and train and compare at least 4 different models. Document these steps well.
- Train (fit, transform, evaluate) multiple models, varying the algorithm and/or hyperparameters you use.
- Compare evaluation metrics across all the models you train and select the ones you want to evaluate using your validate split.
- Feature Selection (after initial iteration through pipeline): Are there any variables that seem to provide limited to no additional information? If so, remove them.
- Based on the evaluation of the models using the train and validate datasets, choose the best model to try with the test data, once.
- Test the final model on the out-of-sample data (the testing dataset), summarize the performance, interpret and document the results.

---

### Conclusion and Next Steps

[(See Executive Summary)](#executive-summary)

---

### Reproduce My Project

---

[(Back to top)](#table-of-contents)
 
- [x] Read this README.md
- [ ] Download the modules (.py files), and final_report.ipynb files into your working directory
- [ ] Download complete dataset from Kaggle at this [link](https://www.kaggle.com/ananaymital/us-used-cars-dataset?select=used_cars_data.csv) and save in same repo as above files
- [ ] Run the final_report.ipynb notebook
