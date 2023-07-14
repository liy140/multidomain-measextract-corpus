# A Multi-Domain Corpus for Measurement Extraction

## Description of contents

A detailed description of corpus creation can be found [here]([arxiv.org](https://aclanthology.org/2023.bionlp-1.1/)).

`finetuning/` 

This folder contains the training and evaluation data for each of the three datasets `measeval`, `bm`, and `msp`. The `measeval`, and `msp` datasets were adapted from the [MeasEval (Harper et al., 2021)](https://github.com/harperco/MeasEval) and the [Material Synthesis Procedual (Mysore et al., 2019)](https://github.com/olivettigroup/annotated-materials-syntheses) corpus respectively.

Each folder contains a `tsv/` and a `jsonl` sub-folder. Each `tsv` file contains annotation information, while each `json` file contains the annotated text and meta information, i.e. the sentence order (`sentId`) and sentence span information. This meta information is especially relevant for the `measeval` and `msp` datasets, as sentence splitting was applied there.

- Explanation on `msp/ignore_sentences.txt`: This file contains a docId-sentenceId pairs that contain of invalid annotations. Partly, invalidity stems from rejection due to high annotation disagreement. Further, there are were sentences that do not contain any entity annotations in the original corpus, but do however contain measurement mentions. However, because they were not annotated in the original corpus, they were not considered by our pre-annotation mapping script that supplied the re-annotation data. We recommend to ignore all sentences here. 

`pretraining/` 

The single txt file in this folder contains data for task-adaptive-pre-training models. It consists of held-out, pooled, unlabeled data related to the three datasets listed above.
In the case of `measeval`, its TAPT data is comprised of paragraphs from the [OA-STM Corpus](https://elsevierlabs.github.io/OA-STM-Corpus/) that were not used for the creation of the MeasEval dataset.

## Citation
```
@inproceedings{li-etal-2023-multi-source,
    title = "Multi-Source (Pre-)Training for Cross-Domain Measurement, Unit and Context Extraction",
    author = "Li, Yueling  and
      Martschat, Sebastian  and
      Ponzetto, Simone Paolo",
    booktitle = "The 22nd Workshop on Biomedical Natural Language Processing and BioNLP Shared Tasks",
    month = jul,
    year = "2023",
    address = "Toronto, Canada",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2023.bionlp-1.1",
    pages = "1--25",
    abstract = "We present a cross-domain approach for automated measurement and context extraction based on pre-trained language models. We construct a multi-source, multi-domain corpus and train an end-to-end extraction pipeline. We then apply multi-source task-adaptive pre-training and fine-tuning to benchmark the cross-domain generalization capability of our model. Further, we conceptualize and apply a task-specific error analysis and derive insights for future work. Our results suggest that multi-source training leads to the best overall results, while single-source training yields the best results for the respective individual domain. While our setup is successful at extracting quantity values and units, more research is needed to improve the extraction of contextual entities. We make the cross-domain corpus used in this work available online.",
}
```
