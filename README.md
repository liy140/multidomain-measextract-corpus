# A Multi-Domain Corpus for Measurement Extraction

## Description of contents

A detailed description of corpus creation can be found [here](arxiv.org).

`finetuning/` 

This folder contains the training and evaluation data for each of the three datasets `measeval`, `bm`, and `msp`. The `measeval`, and `msp` datasets were adapted from the [MeasEval (Harper et al., 2021)](https://github.com/harperco/MeasEval) and the [Material Synthesis Procedual (Mysore et al., 2019)](https://github.com/olivettigroup/annotated-materials-syntheses) corpus respectively.

Each folder contains a `tsv/` and a `jsonl` sub-folder. Each `tsv` file contains annotation information, while each `json` file contains the annotated text and meta information, i.e. the sentence order (`sentId`) and sentence span information. This meta information is especially relevant for the `measeval` and `msp` datasets, as sentence splitting was applied there.

- Explanation on `msp/ignore_sentences.txt`: This file contains a docId-sentenceId pairs that contain of invalid annotations. Partly, invalidity stems from rejection due to high annotation disagreement. Further, there are were sentences that do not contain any entity annotations in the original corpus, but do however contain measurement mentions. However, because they were not annotated in the original corpus, they were not considered by our pre-annotation mapping script that supplied the re-annotation data. We recommend to ignore all sentences here. 

`pretraining/` 

The single txt file in this folder contains data for task-adaptive-pre-training models. It consists of held-out, pooled, unlabeled data related to the three datasets listed above.
In the case of `measeval`, its TAPT data is comprised of paragraphs from the [OA-STM Corpus](https://elsevierlabs.github.io/OA-STM-Corpus/) that were not used for the creation of the MeasEval dataset.
