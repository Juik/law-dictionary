# law-dictionary
Given a law corpus, create a dictionary for similar words looking-up

0.If you only want to try the result, skip process 1,2,3 and directly see 4.

1.You need to make sure your law corpus under this directory. To obtain dataset you can also download from here. (https://drive.google.com/file/d/0B9tRxL7rm9hDTC00b095WndYajQ/view?usp=sharing)

2.Run merge_files.sh and remove_punc.sh you will get the preprocessed corpus, called "merged".

3.Generally, you are supposed to train the model but I've already train the model. If you wanna train the model yourself, you can find my complete code here. (http://www.cs.toronto.edu/~zqiu/resource/law-dic.zip)

4.Assume the model has been trained already. In your terminal, run "./distance vectors.bin" for word or "./distance vectors-phrase.bin". Then you can follow screen instruction to input your target word and the program will return you the closest words and their corresponding distance to your typing word.

A few explanation towards my model:

1.Why use google's word2vec as "framework" instead of gensim or many other version framework(java,etc)?
- Gensim is fabulous. As a python user, I love gensim and done several projects before but gensim only implement skip-gram (no CBOW) and only use softmax (without negative sampling). However, if you really want to try, use the resource below.


C	http://word2vec.googlecode.com/svn/trunk/
python	http://radimrehurek.com/gensim/		 
Java	https://github.com/ansjsun/Word2VEC_java 
C++	https://github.com/jdeng/word2vec

2.What's the parameter I used for training my model?
- Even though word2vec provide CBOW and skip-gram, I still use skip-gram. CBOW is more like "given context, predict the word in the middle", it takes longer and require even bigger corpus.
- The dimensionality of my model is 48.
- the window size is 5, which represents before and after 5 words will be taken into consideration.
- -min-count and -alpha uses default.
- Use hs instead of negtive.
- -binary 1 means use binary to store.



Thanks to:
1. word2vec, google. https://code.google.com/archive/p/word2vec/

2. Tomas Mikolov, google. http://arxiv.org/pdf/1309.4168.pdf

3. Also, University of Toronto professor.
-  Prof. Hinton’s paper “Learning distributed representations of concepts”, 1986.
-  Ryan Kiros, Yukun Zhu, Ruslan Salakhutdinov, Richard S. Zemel, Antonio Torralba, Raquel Urtasun, Sanja Fidler, “Skip-thought vectors”, 2015.
