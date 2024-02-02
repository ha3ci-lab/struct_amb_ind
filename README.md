# STRUCT_AMB_IND

This dataset contains **the first Indonesian speech dataset for structurally/ syntactically ambiguous utterances and each of two disambiguation texts**

## Research Paper
This corpus is part of our study regarding the disambiguation of structurally ambiguous utterances in Indonesian. Our paper, _Speech Recognition and Meaning Interpretation:
Towards Disambiguation of Structurally Ambiguous Spoken Utterances in Indonesian_, has been accepted by EMNLP 2023. If you are using the corpus please cite the following paper:
```
@inproceedings{widiaputri-etal-2023-speech,
    title = "Speech Recognition and Meaning Interpretation: Towards Disambiguation of Structurally Ambiguous Spoken Utterances in {I}ndonesian",
    author = "Widiaputri, Ruhiyah  and
      Purwarianti, Ayu  and
      Lestari, Dessi  and
      Azizah, Kurniawati  and
      Tanaya, Dipta  and
      Sakti, Sakriani",
    booktitle = "Proceedings of the 2023 Conference on Empirical Methods in Natural Language Processing",
    month = dec,
    year = "2023",
    address = "Singapore",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2023.emnlp-main.1045",
    doi = "10.18653/v1/2023.emnlp-main.1045",
}
```

The structurally ambiguous sentences were adapted from Types 4,5,6, and 10 of Types Of Syntactic Ambiguity in English by [[Taha et al., 1983](https://doi.org/10.1515/iral.1983.21.4.251)]. For each chosen type, 100 structurally ambiguous sentences in Indonesian were made by crowdsourcing. Each Indonesian ambiguous sentence has two possible interpretations, resulting in two disambiguation text outputs for each ambiguous sentence. Each disambiguation text is made up of two sentences. All of the sentences have been checked by linguists.

## Directories and files in this corpus
This corpus contains directories as follows.
1. `ind_speech`  
Contains recording results of syntactically ambiguous sentences in Indonesian based on their interpretations. This recording process involved 22 speakers, 2 of them (F01 and M01) are professional speakers and the rest 20 (F02-F11, M02-M11) are undergraduate students. The recordings are grouped by speaker. In total, there are 4800 .wav files.
    >Format of recording files:
    >```
    >ID_F01_Type04_00011.wav
    >```
    > - ID : Language (Indonesian)
    > - (M/F)XX : Male/ female speaker number XX
    > - TypeYY : Type of structural ambiguity (Type04, Type05, Type06, or Type10)
    > - ZZZZV : Syntactically ambiguous sentence no ZZZZ with interpretation no V

2. `text`  
This directory contains 2 files:
    - `ID_amb_disam_text.txt`
    Contains pairs of ambiguous sentences and disambiguation text for each syntactically ambiguous *sentence* in Indonesian. There are 800 rows (400 syntactically ambiguous sentences, each with 2 interpretations):
        ```
        <AMB_SENT_CODE>|<AMB_TRANSCRIPT>|<DISAM_TEXT>
        ID_Type06_00011|saya melihat seseorang di gunung|saya melihat seseorang. saya melihat di gunung
        ```
        - \<AMB_SENT_CODE>: Id for structurally ambiguous sentence and one of its interpretations. Same format with .WAV file, but no speaker ID
        - \<AMB_TRANSCRIPT>: structurally ambiguous sentence
        - \<DISAM_TEXT>: one of <AMB_TRANSCRIPT> interpretation 
    
    - `ID_amb_disam_transcript.txt`
    Contains pairs of ambiguous sentences and disambiguation text for each *recording* file (so it has **4800 rows**). Has a similar format to `ID_amb_disam_text.txt`, but the keys correspond to each recording in the `ind_speech` folder: 
        ```
        <AMB_SENT_RECORD_CODE>|<AMB_TRANSCRIPT>|<DISAM_TEXT>
        ID_F01_Type06_00011|saya melihat seseorang di gunung|saya melihat seseorang. saya melihat di gunung
        ```
        - \<AMB_SENT_RECORD_CODE>: Id for structurally ambiguous utterance and one of its interpretations. Same format with recording filename
        - \<AMB_TRANSCRIPT>: structurally ambiguous sentence
        - \<DISAM_TEXT>: one of <AMB_TRANSCRIPT> interpretation 
    
3. `keys`
This directory contains 3 directories:
    -  `spk_keys`: contains list of <AMB_SENT_CODE> keys for each speaker
    -  `train_dev_test_text_keys`: contains lists of train, dev, and test keys for 400 pairs of structurally ambiguous text and its interpretation
    -  `train_dev_test_spk_keys`: contain lists of train, dev, and test keys for 4800 pair of structurally ambiguous utterance transcription and its interpretation

4. `other`  
Our study in the paper also used additional training data for ASR and SD: a subset of `Indonesian LVCSR news corpus` (https://github.com/s-sakti/data_indsp_news_lvcsr). Therefore, here we also include the corpus's keys we used as train, dev, and test. If you also use the `Indonesian LVCSR news corpus`, don't forget to also cite the papers mentioned on its github.
