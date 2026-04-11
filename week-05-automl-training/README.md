# Week 5: AutoML & No-Code Model Training [cite: 504]
Trained a custom text classifier using Google Colab and compared generic vs fine-tuned Hugging Face models for the Phishing / Threat Detection component of our Network Log Analyzer and Firewall System.

## Custom Model Training 
Built a Phishing vs Legitimate text classifier with a custom dataset using Naive Bayes.
Achieved 66.67% accuracy on 6 held-out test records.
* Precision: 50.00% | Recall: 100.00% | F1: 66.67%

## Fine-Tuned Model Comparison 
Compared 3 models (1 generic + 2 fine-tuned) on 5 test inputs:
* Generic: distilbert-sst-2 (sentiment) 
* Fine-Tuned A: ealvaradob/bert-finetuned-phishing
* Fine-Tuned B: mrm8488/bert-tiny-finetuned-sms-spam-detection 

## Finding [cite: 516]
Recommended ealvaradob/bert-finetuned-phishing for the Phishing / Threat Detection component because it correctly distinguished between actual phishing threats and legitimate IT terminology without triggering false positives. Fine-tuned models showed higher performance with more relevant labels and better handling of edge cases.

See report.md for full analysis.


