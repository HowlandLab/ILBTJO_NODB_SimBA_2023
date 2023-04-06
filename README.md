# ILBTJO_NODB_SimBA_2023
This repository contains data and documentation associated with "High-THC Cannabis smoke impairs working memory capacity in spontaneous tests of novelty preference for objects and odors in rats" (Barnard & Onofrychuk). Specifically, this repository contains project folders assocaiated with classifiers for predicting rat-stimulus interaction for object- and odor-based stimuli, with representative visualizations of model outputs. 

In brief, this project aimed to assess the effects of acute Cannabis smoke exposure on working memory in rats. Here, working memory was inferred by novelty preference on spontaneous interaction tasks with different types (objects and odors) of stimuli. To quantify rat-stimulus interaction, we applied open source pose-estimation (DeepLabCut) and behavioural classification (SimBA) software. This README document will visualize outputs from this pipeline and direct readers to documentation related to model training and testing. A more detailed summary of our methods and performance metrics can be found in the supplementary materials associated with the manuscript preprint (DOI: ).

For both classifiers, we generated pose-estimation data using a single DLC network (DLC version 2.2.3) where eight points of interest were labelled in accordance with the SimBA single animal eight-point configuration. The DLC model and training log associated with this project can be found in the "DLC_model_information" directory. The below figure (created using BioRender and Prism) depicts the placement of points-of-interest, and the mean tracking accuracy for each point, by each video included in the analysis. The full project folder is available upon request.

![Screen Shot 2023-04-05 at 12 43 49 PM](https://user-images.githubusercontent.com/76128217/230175339-a78c24f9-8adb-4ab2-9155-a8b6c0cbf48d.png)

For both classifiers, SimBA (SimBA-UW-tf-dev = 1.32.2) was used and the following hyperparameter set was used for classifier training (n_estimators = 200, RF_criterion = entropy, RF_max_features = sqrt, RF_min_sample leaf = 2). We created six ROIs, where the origin of each circular ROI was placed at the center of stimuli, and extended ~2cm beyond the outermost edge of stimuli. n_estimators = 200, RF_criterion = entropy, RF_max_features = sqrt, RF_min_sample leaf = 2). We slightly deviated from the standard SimBA feature engineering approach by removing ROI-related features called “zone_cumulative_percent” and “zone_cumulative_time”. These features increase the prediction probability of a true class based on animal’s preferentially spending time in a defined ROI. While these features may be useful for predicting behaviors that only include in specific regions (e.g., rat dams retrieving pups from a nest), inclusion of these features in our project would bias predictions unequally between the six stimuli positions. For both classifiers, a discrimination threshold of 0.35 and a minimum bout duration of 50ms was used. 



Interaction with object-based stimuli was operationally defined as frames where the nose is within 2cm of the object, while looking at and/or chewing the stimuli for a duration greater than 50ms. We trained the object classifier on 28,586 frames on human-annotated interaction. The video below depicts pose-estimation and classification predictions on a test (not included in the trainingset) video. The model and assessment files can be found within the "SimBA_object_classifier_information" directory, and targets_inserted csv files (DLC tracking, feature engineering, ROI information, human annotation) can be found at the linked Google Drive. The full project folder is available upon request. (https://drive.google.com/drive/folders/1qIgqLmDf1Q_D6bEagawN5GRccw3Ngcu5?usp=share_link)





https://user-images.githubusercontent.com/76128217/230168849-9ed58960-9e00-4592-a809-acc928f14c2d.mp4





Interaction with odor-based stimuli was operationally defined as framed where the rats’ nose is within 2cm, and within 2cm from the top of the odor jar, looking at and/or chewing the stimuli for a duration greater than 50ms. We trained the odor classifier on 32,872 frames on human-annotated interaction. The video below depicts pose-estimation and classification predictions on a test (not included in the trainingset) video. The model and assessment files can be found within the "SimBA_odor_classifier_information" directory, and targets_inserted csv files (DLC tracking, feature engineering, ROI information, human annotation) can be found at the linked Google Drive. The full project folder is available upon request. (https://drive.google.com/drive/folders/1fMCYBnoaJzRAkUqzPvIPOrlARXW2j1Ae?usp=share_link)





https://user-images.githubusercontent.com/76128217/230211372-9351adaf-e6df-4bf0-9993-fef82736455b.mp4





For a detailed summary of findings, we direct readers to the manuscript preprint and supplemental material; however, we found that behavioural classifications were reliable on the majority of our videoset (~300 5min videos), but manual checking and replacement of automated predictions with stopwatch scoring (~30% videos) was needed. For clarification on experimental procedures or classifier training, please direct questions to the cooresponding author (john.howland@usask.ca).



