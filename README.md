# FakeNewsDetection
Project is to create a Fake news classifier by providing it URLs for which:
a) there is at least one tweet, and
b) where the title and content of the URL is available.

We did not crawl websites to extract HTML. Instead we used this Github repo (github.com/several27/FakeNewsCorpus). It already had the Title and Content for various URLs and these URLs were tagged as being Fake or Reliable (among other tags). There were around 2.0 million "Reliable" and 0.9 million "Fake" URLs. We selected approx. 5,500 data points from these two categories to create a dataset of approx. 11,000 URLs for which feature extraction was done.

Features belong to 4 main groups:
Morphological, Psychological (aka Linguistic), Twitter and Readability.

################################################################################################
DATA files uploaded in the data folder:
1) All_Features_No_Norm.csv -- contains all features
2) M_Features_No_Norm.csv   -- contains only the Morphological features
3) L_Features_No_Norm.csv   -- contains only the Psychological features
4) T_Features_No_Norm.csv   -- contains only the Twitter features
5) R_Features_No_Norm.csv   -- contains only the Readability features
6) MLR_Features_No_Norm.csv -- contains all features EXCEPT Twitter features

Notes: All the data files have the Domain, URL and UrlType. Then the actual feature data starts.
Feature Group          Number of Features (non-Normalised)
Morphological          50
Psychological          93
Twitter                22
Readability            18
Total                  183

################################################################################################

CODE files are uploaded:

1) scriptExtractTweets1.py
Takes an input file for the URLs and extracts all tweets. Uses command line parameters.

2) scriptCreateReadabilityFeatures1.py
Uses a file with URL + Title + Content and processes and creates the Readability features.

3) demoRunFakeNews1.ipynb
Logic:
3a) Starts with the input file containing the URL, Title and Content on which Feature Extraction is to be performed.
Broadly, the logic is to extract tweets. Then using this newly created tweets file and the input file, processing is done to create the four features files (one for each group). Then compbines the individual feature files into one file containing all the features. Note that this combined file has the regular set of features and normalised (using MinMax scaler) values.
3b) Using the All_features file as input now, further subsets of the data are created. These are for excluding and including the normalized values, and for the feature group to be kept in the data subset.
3c) Thus there will be 12 files: All_Features_WITH_norm.csv , All_Features_NO_norm.csv , M_Features_WITH_norm.csv , M_Features_NO_norm.csv , L_Features_WITH_norm.csv , L_Features_NO_norm.csv , T_Features_WITH_norm.csv , T_Features_NO_norm.csv , R_Features_WITH_norm.csv , R_Features_NO_norm.csv , MLR_Features_WITH_norm.csv , MLR_Features_NO_norm.csv.

4) modelTrainingAndCheckAccuracy_without_FeatureSelection.ipynb

5) 4) modelTrainingAndCheckAccuracy_with_FeatureSelection.ipynb

