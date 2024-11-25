## Project Summary
* This project implements a hybrid approach to classify unlabeled news articles into meaningful categories by combining unsupervised topic modeling and supervised text classification using BERT. 
* I have used the following dataset for building my model - https://www.kaggle.com/datasets/rmisra/news-category-dataset.


## Flow Diagram

![Flow Diagram](https://github.com/iPrinka/text-classification/blob/main/assets/flow_chart.jpg?raw=true)

## Approach

Workflow:

    Unsupervised Topic Modeling:
        Leveraged BERTopic to discover latent topics from the news articles.
        Generated interpretable topics using top words and probabilities.
        Example Topics:
            Politics: ["government", "election", "policy"]
            Economy: ["market", "economy", "trade"]

    Pseudo-Labeling:
        Selected high-confidence topic assignments to pseudo-label articles.
        Used these labels as training data for the supervised phase.

    Supervised Learning with TFDistilBertForSequenceClassification:
        Fine-tuned DistilBERT on the pseudo-labeled data for multi-class classification.

    Iterative Refinement:
        Used feedback loops to refine topic modeling outputs and improve labeling.
        Incorporated domain knowledge to handle ambiguous or low-confidence samples.

    Explainability:
        Visualized topics using word clouds for interpretability.
        Cross-checked BERT predictions with topic modeling results to ensure consistency.

## How to use

1. Create a virtual environment (python3 -m venv venv && source venv/bin/activate)

2. Download all the dependencies by running `make requirements` in your terminal

3. Follow the unsupervised.ipynb file to generate pseudo labels using Topic Modeling. Feel free to experiment as per your wish.

4. Once the final input file is generated from topic modeling, follow the supervised.ipynb to create a Supervised Text Classification Model. Note: Model can take hours to build based on your infrastructure. It took me 6 hrs on my macbook.

## Explainability WordCloud Example

![Word Cloud](https://github.com/iPrinka/text-classification/blob/main/assets/wordcloud.png?raw=true)

## Output

![Output](https://github.com/iPrinka/text-classification/blob/main/assets/output_sample.png?raw=true)
