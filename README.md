# Word Embeddings
Using Word2Vec to analyse popular literature and study how neural networks learn correlations.

## Data
In this implementation, I used two of my favourite fictional books:
1. Harry Potter (7 volumes) by J.K.Rowling
2. A Song of Ice and Fire (5 volumes) by George RR Martin

## Neural Embeddings
Traditional natural language processing systems treat words as discrete atomic symbols, by representing each word in vocabulary by a unique token/id. These encodings are arbitrary, and provide no useful information to the system regarding the relationships that may exist between the individual symbols. This means that the model can leverage very little of what it has learned about say, 'cats' when it is processing data about 'dogs' (such that they are both animals, four-legged, pets, etc.).

Representing words as unique, discrete ids furthermore leads to data sparsity, and usually means that we may need more data in order to successfully train statistical models. Using vector representations can overcome some of these obstacles.

**Vector space models (VSMs)** represent (embed) words in a continuous vector space where semantically similar words are mapped to nearby points ('are embedded nearby each other'). The task of vectorizing can be classified into two broad topics:
1. Count based (eg. LSA)
2. Prediction based (eg. Neural Probabilistic Models)

Here we are focussing on the latter models. Word2Vec is computationally-efficient predictive model for learning word embeddings from raw text. We build a neural network that either tries to predict a target word given context words around it (*Continuos Bag of Words model*) or predict the context words given a particular word (*Skip gram model*).

**I have used the Skip Gram model in this work**, because each context-target pair is considered as a new observation in Skip Gram models, which tend to do better when we have larger datasets.

Word embeddings, as the name suggests, embed different symbols in a reduced dimension space. This tends to reduce the dimensionality of the data, while clustering contextually similar words together.
This leads to the model being able to extract useful relations from the text corpus. 

In the following section, I present a few intriguing results, which give an illusion that the trained neural network has understood the books really well!

## Results

**Some analogies for Harry Potter books:**

Slytherin is related to Malfoy, as **Gryffindor** is related to Harry

Vernon is related to Petunia, as **James** is related to Lily

Sirius is related to Regulus, as **George** is related to Fred

Dobby is related to Malfoy, as **Kreacher** is related to Black

Given the relation we are looking for in the first part of the sentence, the model was able to predict the highlighted entity with same relation as the last entity in the sentence.

**Similarly for Game of Thrones, interesting analogies are presented below:**

Winterfell : Stark :: Riverrun : **Tully** 

Jaime : hand :: Tyrion : **wine** (Quite Hilarious!)

Nymeria : Arya :: dragons : **Dany**

Needle : Arya :: Oathkeeper : **Brienne** 

Nymeria : Arya :: Summer : **Bran** 

Catelyn : Arya :: Cersei : **Joff** 

Sansa : Arya :: Tommen : **Joffrey**

Renly : Stannis :: Eddard :  **Benjen**

The results seem really interesting, as the model has successfully learnt inherent relationships between different characters of the story.

But the most amazing part was the last prediction I tried with the model. The model was able to give a spoiler, which majority audience did not know until the last episode of Season 6 of the corresponding TV Show. If you still aren't aware of this, and do not want a **spoiler**, I request you to turn back if you can (sadly I couldn't!)

Catelyn is related to Ned, as **Lyanna** is related to Rhaegar

Interestingly, *Rhaegar's wife was Elia Martell*, but the model predicted Lyanna Stark. Did it just understand love?!
