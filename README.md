# Tibetan-English-OpenNMT-tf-Google-Colab-Notebook-
Use OpenNMT-tf with Google Colab Notebook to translate from Tibetan to English with a 32,000 SentencePiece vocab

Essentially, the notebook(s) provide a "ready to use out of the box" notebook for new users who want to make use of Google Colab and OpenNMT to translate from Tibetan to English.

Note: The reason a plural "notebook(s)" is used is to account for the different notebooks that accomplish similar but unique tasks (e.g., (a) build the SentencePiece model and vocab files, (b) to train the OpenNMT model and (c) to make inferences off a test set. These could of course be put in the same notebook but would be cumbersome and a bit unruly).

The notebook(s) connects with Google Drive for the data files (the data is included in this repo)
The notebook(s) downgrades TF (current Google Colab builds come installed with TF 2.15) since at the time of my project OpenNMT is compatible with TF builds up through 2.13.
The notebook(s) install cuda and cudnn so that GPUs can be utilized (this notebook utilzed a single A100 GPU which worked fine and ran to completion [i.e. no improvement on BLEU score after multiple evaluation cycles]). There is a link at the top of the notebooks on getting started with multiple GPUs if you would like to try that.
The notebook(s) installs and builds the SentencePiece command line tools from C++ source (we won't use "pip install sentencepiece") for reasons explained in OpenNMT repo listed above.

Steps to use this notebook with Google Drive and Google Colab:

1) Create a folder on Google Drive (e.g., tib_poen_32K_vocab)
2) Change directory so that you are inside tib_poen_32K_vocab
3) Create two more folders: config and data
4) Inside config directory, place the .yml file
5) Run the PrepareData_NMT.ipynb to create your train/validation/test data sets for both Tibetan (po) and English (en)
6) Run the trainSentencePieceModel_32Kvocab_poen.ipynb to create your SentencePiece vocab and model files
7) Run the PO_EN_NMT_32Kvocab.ipynb to train, evaluate, etc
