# Biomedical Word Embeddings for Spanish: Development and Evaluation

This repository contains the biomedical word embeddings generated from Spanish corpora.

## Digital Object Identifier (DOI) and access to files

https://doi.org/10.5281/zenodo.3626806

## Directory Structure

The example below shows the structure for the Wikipedia subset with 50 dimensions. All other subsets have the same structure

<pre>
Wikipedia/
    50/
        W2V_wiki_w10_c5_50_15epoch.txt: Word2Vec in text file
        wiki_w10_c5_50_15epoch.w2vmodel: Word2Vec in gensim file
        wiki_w10_c5_50_15epoch.w2vmodel.trainables.syn1neg.npy: Word2Vec in gensim file
        wiki_w10_c5_50_15epoch.w2vmodel.wv.vectors.npy: Word2Vec in gensim file
    Wikipedia_Fasttext.bin: fastText embedding in binary file.
    Wikipedia_Fasttext.vec: fastText embedding in text file.
</pre>


## Corpora used

* Scielo Full-Text in Spanish: We retrieved all the full-text available in Scielo.org (until December/2018) and processed them into sentences. Scielo.org node contains all Spanish articles, thus includes Latin and European Spanish.
  * Sentences: 3,267,556
  * Tokens: 100,116,298
* Wikipedia Health: We retrieved all articles from the following Wikipedia categories: Pharmacology, Pharmacy, Medicine and Biology. Data were retrieved during December/2018.
  * Sentences: 4,030,833
  * Tokens: 82,006,270
* Scielo+Wikipedia Health: We concatenated the previous two corpora.

## Embeddings generation

Two different approaches were used: [Word2Vec](https://github.com/tmikolov/word2vec) and [fastText](https://fasttext.cc/) .

### Word2Vec

We used the python [Gensim package](https://radimrehurek.com/gensim/index.html) to train different Word2Vec embeddings.
The following configurations were set:
* Embedding dimension: 50, 150 and 300.
* Epochs 15
* Window size: 10
* Minimum word count: 5
* Algorithm: CBOW
* Copora: Scielo, Wikipedia and Scielo+Wikipedia

### fastText

We used the [fastText](https://fasttext.cc/) to train word embeddings.
We kept all standard options for training.
The following corpora were used: Scielo, Wikipedia and Scielo+Wikipedia

## Evaluation

Evaluation was carried out by both extrinsic (with a Named Entity Recognition framework) and intrinsic, with the three already available datasets for such task UMNSRS-sim, UMNSRS-rel, and MayoSRS.  
With NER, we defined that the best model was with 300 dimensions, and projected the words using Principal Component Analysis.

Further details about evaluation and the steps performed can be found in our [paper](Biomedical_Word_Embeddings_for_Spanish__Development_and_Evaluation.pdf) in this respository.

The PCA plots for our embedding and a general-domain embedding are available in this repository also:

* [Our embeddings](our_embeddings.pdf)
* [SBWC embeddings](sbwc_embeddings.pdf)

The translations for Spanish in TSV format of the UMNSRS and Mayo datasets one are also availabe in this Github repository:

* [UMNSRS Similarity](UMNSRS_Similarity_Filtered.tsv)
* [UMNSRS Relatedness](UMNSRS_Relatedness_Filtered.tsv)
* [Mayo](Mayo_Filtered.tsv)


## Contact

Felipe Soares (felipe.soares@bsc.es)

## License

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.

Copyright (c) 2018 Secretaría de Estado para el Avance Digital (SEAD)

## Citation

```@article{Soares2019,
author = "Felipe Soares and Marta Villegas and Aitor Gonzalez-Agirre and Martin Krallinger and Jordi Armengol-Estapé",
title = "{Biomedical Word Embeddings for Spanish: Development and Evaluation}",
year = "2019",
month = "4",
url = "https://figshare.com/articles/Biomedical_Word_Embeddings_for_Spanish_Development_and_Evaluation/7807928",
doi = "10.6084/m9.figshare.7807928.v2"
}
```

## Disclaimer

The models published in this repository are intended for a generalist purpose and are available to third parties. These models may have bias and/or any other undesirable distortions.

When third parties, deploy or provide systems and/or services to other parties using any of these models (or using systems based on these models) or become users of the models, they should note that it is their responsibility to mitigate the risks arising from their use and, in any event, to comply with applicable regulations, including regulations regarding the use of artificial intelligence.

In no event shall the owner of the models (SEDIA – State Secretariat for digitalization and artificial intelligence) nor the creator (BSC – Barcelona Supercomputing Center) be liable for any results arising from the use made by third parties of these models.


Los modelos publicados en este repositorio tienen una finalidad generalista y están a disposición de terceros. Estos modelos pueden tener sesgos y/u otro tipo de distorsiones indeseables.

Cuando terceros desplieguen o proporcionen sistemas y/o servicios a otras partes usando alguno de estos modelos (o utilizando sistemas basados en estos modelos) o se conviertan en usuarios de los modelos, deben tener en cuenta que es su responsabilidad mitigar los riesgos derivados de su uso y, en todo caso, cumplir con la normativa aplicable, incluyendo la normativa en materia de uso de inteligencia artificial.

En ningún caso el propietario de los modelos (SEDIA – Secretaría de Estado de Digitalización e Inteligencia Artificial) ni el creador (BSC – Barcelona Supercomputing Center) serán responsables de los resultados derivados del uso que hagan terceros de estos modelos.

