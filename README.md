# Uncertainity_Aware_Paraphrase_Plagiarism_Detector
## Project Overview
Large language models (LLMs) can rapidly re-paraphrase source text in ways that evade traditional string-matching plagiarism checkers. Exponential growth of LLM‑generated text raises authenticity concerns, so our goal is to build a reproducible pipeline that generates watermarked paraphrases and trains a classifier to spot plagiarized text. 
![plagiarism detection](https://github.com/GAYATRI-SIVANI-SUSARLA/LLM_PROJECT/blob/main/photos/Screenshot%202025-05-29%20121226.png)
## Objective
This project investigates the dual problem of 
1. Generating machine paraphrases with a lightweight LLM
2.  Detecting such paraphrases using both conventional services and fine-tuned Transformer classifiers.
Building on recent research on
machine-paraphrased plagiarism, watermarking for LLMs, and paraphrase detection,
We fine-tune T5-small to create paraphrases over the 262k-example Autoregressive
Paraphrase the Dataset, and train a RoBERTa-base model to differentiate
original from machine-generated text.
### Our project RoadMap
![Roadmap](https://github.com/GAYATRI-SIVANI-SUSARLA/LLM_PROJECT/blob/main/photos/Screenshot%202025-05-29%20121948.png)
## Methods
### Watermark Technique
Greenlist tokens - A Subset of tokens is selected based on pseudo random function
Statistical Detection - Measure frequency of the tokens, higher than expected frequency indicate the presence of a watermark, the watermark can be detected with high confidence as few as 25 tokens.
The watermark method does not degrade text quality
### Watermarking paraphrase generation
Model: facebook/opt‑1.3b
Tokenization with Hugging Face AutoTokenizer
Integrate WatermarkLogitsProcessor (gamma = 0.25, delta = 2.0, self‑hash seeding)
Output length ≈ 2× original tokens
### Parapharse detection model
Base encoder: RoBERTa
Binary classification: original vs. plagiarized
Fine-tuned the model with the dataset, then tested it on 100 sentences by generating paraphrases of these sentences
Evaluated clarity (bleu score), fluency (textblob), coherence(cosine similarity)
Detected the plagiarism using tools Roberta (itself), Turnitin, Copyscape, and calculated F-1 score for these tools.

## Dataset
 We took the dataset from the 🤗[HuggingFace](https://huggingface.co/) we used dataset: The Machine Paraphrase Corpus (MPC) consists of ~200k examples of original and paraphrases using two online paraphrasing tools. It uses two paraphrasing tools (SpinnerChief, SpinBot) on three source texts (Wikipedia, arXiv, student theses). More details [Dataset](https://huggingface.co/datasets/jpwahle/machine-paraphrase-dataset)
 
## Code
## Conclusion
