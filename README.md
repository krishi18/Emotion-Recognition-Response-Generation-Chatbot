# Emotional Sentiment Analysis and Adaptive Response System
 Develop a prototype chatbot capable of identifying the emotional state of a user based on a conversation and responding with culturally relevant and empathetic responses.

### Link to dataset:
https://www.kaggle.com/datasets/debarshichanda/goemotions/data

### Approach:
 
This project integrates emotion recognition with adaptive response generation to create an emotionally intelligent conversational chatbot. Starting with preprocessing the dataset “GoEmotion” like treating null values, one-hot encoding etc. and further used preprocessing techniques to standardize text (e.g., removing stop words, punctuation), tokenized and prepare it for training purposes. For training, I had used a pre-trained DistilRoBERTa language model version and fine tuned using the pre-processed training dataset. After training, predictions were made based on the test data and accuracy was evaluated based on true and predicted labels. For response generation, I had used a pre-trained GPT2 model fine tuned for response generation and generated curated responses based on the input text given after identifying the targeted emotion. 
Data Preparation techniques:
GoEmotions is a corpus of 58k carefully curated comments, with human annotations to 28 emotion categories. I mapped them to 7 core emotions which included anger, disgust, fear, joy, sadness, surprise and neutral using Ekman mapping.
•	Treated all the null values.
•	Defined a function called EmotionMapping and created a column consisting of the mapped emotions and one-hot encoded all the emotions into separate columns with binary values. Emotions were mapped to consistent labels (e.g., joy → happy, sadness → sad).
•	Preprocessed the [‘Text’] column for removing stopwords, punctuation and performing stemming. 
•	Class distributions were balanced using oversampling techniques to avoid bias.

### Model Choices:

Two models were utilized here:
1.	michellejieli/emotion_text_classifier: The model is a fine-tuned version of Emotion English DistilRoBERTa-base and DistilRoBERTa base- a transformer model that performs sentiment analysis. I fine-tuned the model on transcripts from the Friends show with the goal of classifying emotions from text data, specifically dialogue from Netflix shows or movies. The model predicts 6 Ekman emotions and a neutral class. 
2.	SuramyaPokharel/gpt2-response_gen: This model is a fine-tuned version of google/flan-t5-base on an unknown dataset for adaptive response generation.

### Challenges faced:

1.	Emotion Prediction: Overlap in emotional expressions (e.g., anger vs. fear).
2.	Response Generation: Ensuring emotion alignment in responses.
3.	Improving accuracy of the model.

### Results:

1.	Accuracy: 60.59%
2.	Training Loss: 0.438
3.	Validation Loss: 1.442

