# ProjectGlutenberg_NLP

Dataset downloaded from: https://www.gutenberg.org

## Features
Our features for this model were a bag of words for the pronouns, determiners, and punctuation marks, as well as the average number of words per sentence.

We also tried using just adjectives, pronouns, and determiners as the features and the result was extremely disapointing. Using the SVM model, while the accuracy for the validation data was around 72 percent, it was only around 8 for the real testing data. With KNN, the former was about 74 percent and the latter was 17 percent. From this, we concluded that the specific words used by the authors are one of the most significant features.

### Pronouns and Determiners
Researchers have found that women tend to use more pronouns in writing to talk about relationships. Women also use pronouns to establish a relationship with the reader. Men, on the other hand, write more about objects, leading to a higher use in determiners. The pronouns and determiners used in writing could thus distinguish between male and female authors.

### Punctuation Marks
This analysis of men and women writers states that because men tend to write about objects and facts, they write more concise sentences. Similarly, since women tend to establish relationships with the readers, they tend to write longer sentences. This would lead to a difference in their uses of punctuation marks. Punctuation had the biggest impact on the accuracy of the model.

### Words per Sentence
Since men tend to write more concisely than women, their sentences will be shorter and have fewer words. Therefore, the average number of words per sentence could distinguish between male and female writers.

### Adjectives
We initially decided to have adjectives as one of our features. However, we found that excluding this would increase our accuracy, so we dropped it as a feature. This is likely because men and women use adjectives in a similar manner.

## Preprocessing
For women’s books, we filtered out the words “Finis” and “The end” at the end because they don’t add anything of value. For the men’s books, we removed footnotes at the end and underscores in the middle of the texts. For all the books, we removed extremely long sentences. We then split each book into documents of ten sentences each.

We found that making everything lowercase or lemmatizing the text didn’t have any effect on the accuracy, which means that the location the words were used didn’t have an impact.

We chose to not remove stop words because many stop words are pronouns or determiners, which are our features.

## Model
We saw in this research paper that an svm model with a linear kernel can achieve quite accurate results, so we initially decided to use an svm model. Later on, we also wanted to test KNN to see whether or not it’s more accurate, but didn’t have time to test it on our final features. We tried different values of C for our svm model and found that C=0.1 and C=1 achieve similar accuracies of around 95% accurate.

80% of our data was used as training data and the remaining 20% was our validation data. The 95% accuracy is on our validation data.

Our testing data is one book split into multiple documents of 10 sentences each. Our model predicted that around 90% of the documents were written by a woman.

## Conclusion
We found that the most accurate method is a linear svm model with words per sentence and bag of words on pronouns, determiners, and punctuation as the features. This model without bag of words is not at all accurate, possibly because men and women generally use certain words with different frequencies. If we had more time, we would try using the same features on a KNN model.
