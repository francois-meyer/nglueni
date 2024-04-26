# NGLUEni:  Benchmarking PLMs for Nguni Languages

Paper: *NGLUEni: Benchmarking and Adapting Pretrained Language Models for Nguni Languages*, Francois Meyer, Haiyue Song, Abhisek Chakrabarty, Jan Buys, Raj Dabre and Hideki Tanaka, LREC-COLING 2024

NGLUEni is a benchmark for evaluating pretrained language models (PLMs) for the Nguni languages - isiXhosa (**xh**), isiZulu (**zu**), isiNdebele (**nr**), and Siswati (**ss**). It covers natural language understanding and generation, spanning 6 tasks and 11 datasets. This is a centralised repository to access all the datasets in the NGLUEni evaluation suite. 


&nbsp;
# Natural Language Understanding (NLU)

NGLUEni is a collection of existing, publicly available Nguni datasets. Most of these datasets are already preprocessed and split into train/valid/test sets for finetuning. However, some of the datasets (SADiLaR NER, NCHLT Genre, NCHLT PC) are publicly available as raw annotated datasets (not separated into training and evaluation sets), so we have split these into standardised train/valid/test sets (80%/10%/10%) and released these splits for reproducibility (see [standardised-data](https://github.com/francois-meyer/nglueni/tree/main/standardised-data)). The following table summarises the NLU tasks in NGUEni.


| Task                | Dataset       | xh | zu | nr | ss | NGLUEni version |  
|---------------------|---------------|----|----|----|----|------ |
| NER                 | MasakhaNER    | ✓  | ✓  |    |    |  [Original dataset](https://github.com/masakhane-io/masakhane-ner) |
|                     | SADiLaR NER   | ✓  | ✓  | ✓  | ✓  | [NGLUEni standardised split](https://github.com/francois-meyer/nglueni/tree/main/standardised-data/nlu/sadilar-ner) |
| POS tagging         | MasakhaPOS    | ✓  | ✓  |    |    |  [Original dataset](https://github.com/masakhane-io/masakhane-pos) |
|                     | NLAPOST       | ✓  | ✓  | ✓  | ✓  | [Original dataset](https://repo.sadilar.org/handle/20.500.12185/546) |
| Classification      | MasakhaNEWS   | ✓  |    |    |    |  [Original dataset](https://github.com/masakhane-io/masakhane-news) |
|                     | ANTC          | ✓  |    |    |    |   [Original dataset](https://github.com/uds-lsv/afro-maft/tree/main/dataset/ANTC) |      
|                     | NCHLT Genre   | ✓  | ✓  | ✓  | ✓  | [NGLUEni standardised split](https://github.com/francois-meyer/nglueni/tree/main/standardised-data/nlu/nchlt-genre) |
| Phrase chunk        | NCHLT PC      | ✓  | ✓  | ✓  | ✓  | [NGLUEni standardised split](https://github.com/francois-meyer/nglueni/tree/main/standardised-data/nlu/nchlt-pc)  |


&nbsp;
# Natural Language Generation (NLG)


The existing options for evaluating Nguni NLG are limited to machine translation and isiXhosa data-to-text. To enable more NLG evaluation we have adapted two existing Nguni news datasets (MasakhaNEWS  and Vuk'uzenzela) for the task of generating headlines based on article text. The following table summarises the NLG tasks in NGUEni.



| Task                | Dataset       | xh | zu | nr | ss | NGLUEni version |
|---------------------|---------------|----|----|----|----|------|
| Data-to-text        | T2X           | ✓  |    |    |    | [Original dataset](https://github.com/francois-meyer/t2x) |
| Headline generation | MasakhaNEWS   | ✓  |    |    |    | Text-headline pairs in [original dataset](https://github.com/masakhane-io/masakhane-news)  |
|                     | Vuk'uzenzele  | ✓  | ✓  | ✓  | ✓  | [NGLUEni extracted text-headline pairs](https://github.com/francois-meyer/nglueni/tree/main/standardised-data/nlg/vukuzenzele-headline-generation)  |


[MasakhaNEWS](https://github.com/masakhane-io/masakhane-news) is a news topic classification dataset. The data is stored as tables that contain separate columns for the article text and headline, which we use to extract text-headline pairs for an isiXhosa headline generation task.


[Vuk'uzenzele](https://github.com/dsfsi/vukuzenzele-nlp) is an unannotated text dataset that was created by scraping the South African government news magazine Vuk'uzenzele. It contains government news articles in all 4 Nguni languages. We automatically extract article-headline pairs and manually remove erroneously processed examples. The datasets are too small for finetuning (around 150 examples per language), so we only use them to _evaluate_ models finetuned on MasakhaNEWS headline generation. MasakhaNEWS and Vuk'uzenzele cover different domains and languages, so this tests cross-domain and zero-shot cross-lingual performance.