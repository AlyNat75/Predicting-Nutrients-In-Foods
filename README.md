# Overview
A research project with a PhD Candidate at WashU's Visual Data Analytics Lab, involving predicting the existence of common nutrients in a food given its ingredients list.

- Used language processing to convert the ingredients lists to numerical vectors (input), along with USDA nutrient data (ground-truth output), to train a multilabel classifier model
- Worked with TensorFlow, Keras, and Scikit-Learn

# Research Abstract

Predicting Nutrient Values in a Food Given its Ingredient List
Consumers rely on food nutrition fact labels to determine if products fit into their dietary
goals. Food manufacturers have the responsibility to display accurate nutrient data on these
labels as standardized by the Food and Drug Administration (FDA). In doing so, they rely on
digital tools which take nutrition data as an input and generate the standardized labels. However,
this process is prone to human errors in the inputs and current tools do not detect such errors. For
example, a manufacturer may enter 0 grams of sugar for a cookie product that contains sugar in
its ingredient list. If left undetected, this false information could be a major problem for
consumers such as diabetics.

The goal of this project is to outline a solution to this problem. Using a machine learning
approach and data from the USDA Branded Food Products Database, the existence of nutrients
in a food can be predicted given their ingredient list. If the algorithm predicts that a nutrient is in
a food, it can validate the entries for such nutrients and communicate inconsistencies to the users
via the interface.

Using an off-the-shelf natural language processing technique (word2vec), we mapped the
list of ingredients into a 100-dimensional numerical space. This is a similar approach that a
Slovene study used when predicting macronutrient values (carbohydrates, fat, protein, water) in a
food given a short description (Ispirova, Eftimov, Seljak). Turning ingredient lists into numerical
vectors meant that foods with similar ingredients had similar vectors and when plotted on a
cartesian plane (after applying dimensionality reduction), many similar groups of foods such as
meats or pastas appeared within a close proximity of one another. These numerical vectors
(input), along with the nutrient data from the USDA (ground-truth output), were used to train and
test a classification model, specifically a multi-label classifier. Multi-label classification was
used as it was able to make 12 binary predictions for an entire food’s nutrients.

There were many different metrics that we used to evaluate our classification model such
as ROC curves and accuracy (% measure of prediction accuracy for a nutrient). Majority of
nutrient’s accuracies fell within 80%-95% and AUCs (area under the ROC curve) fell within
0.85-0.90 with valuers closer to 1 being desired. Some notable outlier nutrients were Energy
(calories) which had an accuracy of about 99% and an AUC 0.945, most likely due to the fact
that almost all foods have calories. The worst nutrient was Calcium which has an accuracy of
0.72 and an AUC of 0.85 most likely due to the lack of calcium data for most foods.

While these evaluation metrics show that the classification model was decently accurate
in predicting individual nutrients, we observed a lower performance predicting all 12 nutrients in
a given food. On average, 10.79 nutrients are predicted accurately meaning the model tends to
get 1-2 nutrient predictions wrong per food. Further investigation revealed that our model could
accurately predict every nutrient value accurately only 37% of the time.

In the future we would like to further refine our model to predict the combination of
nutrients accurately. This shortcoming of our model, if deployed in the real-world, could result in
mistrust and frustration for users. Some ways that this could be implemented is to use more
training data to allow the model to see more variations of foods with varied ingredients.
Additionally, nutrients like calcium with low accuracies could also be eliminated as the USDA
data set doesn’t have enough foods with calcium to train with. For now, this model serves as a
benchmark for future improved models taking into account the need for higher accuracy.
