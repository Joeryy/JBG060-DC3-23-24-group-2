# South Sudan Project 
## Code description

### Hand-labeling
_articles_from_district.ipynb is the first notebook. This notebook takes all the articles from _articles_summary_cleaned.csv_ and assigns the closest county to it. furthermore it filters the articles to only include Rubkona, Koch, and Gorgial East Articles. This becomes _articles_summary_cleaned_with_location.csv_

_topic_modelling.ipynb_, A BERTopic model is fit on _articles_summary_cleaned_with_location.csv_ then four categories/keywords (hunger, refugees, humanitarian, and conflict) are defined. These categories are used for categorising articles (or none if the article doesn’t match any of the categories). The conflict category will be used to filter down the number of articles that we as a group handlabeled

Next _named_entity_recognition.ipynb_ was used for handlabelling data. The first section of the notebook uses spacy which allowed us to pick up on key words and locations while manually labeling the articles from _articles_summary_cleaned_with_location.csv_.

The results of our handlabelling is in _article_handlabeled_v2_raw.csv_.Running the rest of the _named_entity_recognition.ipynb_ notebook will clean the handlabeled data and preprocess it for the input for the linear regression _merged_df_for_causality_v2.csv_

### Confounding Variables
_climate_investigation.ipynb_ looks into the cross correlations between climate variables and IPC scores. Provides insight into climate variables.

_BERTopic_2014_spikes.ipynb_ attempts to find additional confounding variables mentioned in the articles. No additional confounding variables found beesides violence.


### OLS, Sensitivity Analysis, and Causal Analysis
_Final_OLS_models.ipynb_ creates 4 OLS models based on Granger Causality to explain how conflict events have lasting effect and hence a new model must be trained after such an event MSE scores used as metric.

_sensitivity_analysis.ipynb_ checks the importance of the parameters in the Linear Regression. Confirming that complexity is optimal

_TS_Causal_impact_final.ipynb_ notebook implements Bayesian Structural Time Series Model from Google to see if an event had a causal impact. In our case if the Bentiu takeover had a causal impact on the ipc scores while controlling for the confounding variable of Climate


## Requirements
To install the requirements open Terminal (macOS)/Command Prompt (Windows) and run pip install -r requirements.txt. If you create a new environment in PyCharm, an icon should appear to install requirements. The code runs with Python 3.9.16.

Required libraries:
- bertopic == 0.15.0 
- pandas == 1.4.4 
- geopandas == 0.13.2 
- matplotlib == 3.7.2 
- seaborn == 0.12.2
- statsmodels == 0.14.0

For Spacy:
pip install -U pip setuptools wheel
pip install -U spacy
python -m spacy download en_core_web_sm

## Troubleshooting

If you encounter any issues while running the notebooks, try the following:
- check that you have all the necessary libraries installed and the correct versions of them
- check your Python version. In principle, the code should work with any Python versions higher than 3.9.16. If this is not the case, create a virtual environment that uses Python 3.9.16.
- check that the models folder exists (for placeholder _blank_ was placed in the folder)
- delete all contents in models folder
- issues with installing spacy go to: https://spacy.io/usage
