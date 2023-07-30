# Translation and Word Meanings
## Requirements

- Python 3.8.8

## Dependencies

1. Create and activate a virtual environment (replace "myenv" with a name of your choice):

On macOS and Linux:
```
python3.8 -m venv myenv
source myenv/bin/activate
```

On Windows:
```
python3.8 -m venv myenv
source myenv/bin/activate
```

2. Install the required packages, including the specific Python version:
```
pip install -r requirements.txt
```
## Results
### Monolingual Disambiguation
#### State-of-the-art 2014
Using the [Gold Standard](GoldStandard/monolingual/eng2014.csv) extracted following the methodology used in the state-of-the-art research in 2014
```
python monolingual/stoa2014.py 2014
```
Using the [Gold Standard](GoldStandard/monolingual/eng2023.csv) annotated by our annotators
```
python monolingual/stoa2014.py 2023
```
#### FastText
Using the Gold Standard extracted following the methodology used in the state-of-the-art research in 2014
```
python monolingual/FastText_mono.py 2014
```
Using the Gold Standard annotated by our annotators
```
python monolingual/FastText_mono.py 2023
```
#### Sentence Embedding
Short versions for sentence embedding models:
stsb: stsb-xlm-r-multilingual (sentence bert)
paraphrase: stsb-xlm-r-multilingual (sentence bert)
labse: Language-Agnostic BERT Sentence Embedding
muse: multilingual universal sentence embedding
laser: Language-Agnostic SEntence Representations)
The evaluation dataset is set as the [Gold Standard](GoldStandard/monolingual/eng2023.csv) annotated by our annotators.
For example, utilizing paraphrase-multilingual-mpnet-base-v2 (sentence bert).
```
python monolingual/sentence_embedding_mono.py paraphrase
```
### Multilingual Disambiguation
#### FastText
In the context of Multilingual Disambiguation, the ISO 639-2/T code is utilized to specify a particular target language. For instance, to generate results solely for French, you would execute the following command:
```
python multilingual/FastText_multi.py fra
```
On the other hand, if you intend to produce results for all the target languages, including French, Italian, German, Spanish, Chinese, and Russian, you should use the 'all' option like this:
```
python multilingual/FastText_multi.py all
```
#### Sentence Embedding
ISO 639-2/T code and short versions for sentence embedding models are both used as arguments. To obtain the results only for French using stsb-xlm-r-multilingual (sentence bert), run:
```
python multilingual/sentence_embedding_multi.py fra --model stsb
```
For all target languages using paraphrase: stsb-xlm-r-multilingual (sentence bert), run:
```
python multilingual/sentence_embedding_multi.py all --model paraphrase

```
#### Sentence embedding combining machine translation system
When target language is French and using stsb-xlm-r-multilingual (sentence bert), run:
```
python multilingual/sbert_translate.py fra --model stsb
```
For all target languages using paraphrase: stsb-xlm-r-multilingual (sentence bert), run:
```
python multilingual/sbert_translate.py all --model paraphrase
```
