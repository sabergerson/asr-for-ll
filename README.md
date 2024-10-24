## ASR for Language Learning with Whisper

This repository contains code for fine-tuning and evaluating OpenAI's [Whisper](https://github.com/openai/whisper) using two ASR datasets, [EdAcc](https://groups.inf.ed.ac.uk/edacc/) and [UME-ERJ](https://research.nii.ac.jp/src/en/UME-ERJ.html). EdAcc contains multi-accented conversational English speech, and UME-ERJ contains Japanese-accented read English speech. This code was developed as part of a thesis project at UCL in collaboration with DMM Eikaiwa. The purpose of the code is to evaluate the resulting models on Japanese-accented conversational English speech data collected and annotated by DMM Eikaiwa. The corresponding datasets and models for this code can be found at [huggingface.co/sage-bergerson](https://huggingface.co/sage-bergerson). All code, data, and models relating to or using data collected by DMM Eikaiwa are not public.   

For environment set up instructions see the folder setup.  

#### High-level folder contents:

- edacc: Python files for processing EdAcc data, fine-tuning Whisper using processed EdAcc data, and evaluating Whisper zero-shot and after fine-tuning on EdAcc data.   

- setup: Instructions for installing required packages for data processing, fine-tuning and evaluation with SCLITE via the terminal.  

- ume_erj: Python files for processing UME-ERJ data, fine-tuning Whisper using processed UME-ERJ data, and evaluating Whisper zero-shot and after fine-tuning on UME-ERJ data.   

- whisper_utils: Python and JSON files from [Whisper](https://github.com/openai/whisper) used for transcript standardization.

#### Guide to all folders & files:

- edacc/data_processing: Python files for processing EdAcc data for use with Whisper.  

  - edacc/data_processing/edacc_raw.ipynb: Standardizes and formats EdAcc data for evaluations with Whisper. Uploads data to HuggingFace.
  - edacc/data_processing/edacc_whisper.ipynb: Applies Whisper pre-processing to prepare EdAcc data for use in Whisper fine-tuning. Uploads data to HuggingFace.  

- edacc/ft: Python files for running Whisper fine-tuning and evaluation with EdAcc data and text files of reference data, predictions, and WER results.

  - edacc/ft/EdAcc1000/ft_run/edacc_ft.ipynb: Runs fine-tuning with EdAcc dev set for 1000 iterations. 
  - edacc/ft/EdAcc4000/ft_run/edacc_ft.ipynb: Runs fine-tuning with EdAcc dev set for 4000 iterations. 
  - edacc/ft/EdAcc4000/output/ft_predictions.txt: EdAcc test set transcripts predicted by Whisper fine-tuned on EdAcc dev set for 4000 iterations.
  - edacc/ft/EdAcc4000/output/ft_references.txt: EdAcc test set reference transcripts.
  - edacc/ft/EdAcc4000/output/sclite/ft_results.txt: WER and results breakdown computed by SCLITE for EdAcc test set using Whisper fine-tuned on EdAcc dev set for 4000 iterations.
  - edacc/ft/EdAcc4000/edacc_test.ipynb: Produces EdAcc test set predicted transcripts using Whisper fine-tuned on EdAcc dev set for 4000 iterations.
  - edacc/ft/EdAcc600/ft_run/edacc_ft.ipynb: Runs fine-tuning with EdAcc dev set for 600 iterations. 
  - edacc/ft/EdAcc600/output/ft_predictions.txt: EdAcc test set transcripts predicted by Whisper fine-tuned on EdAcc dev set for 600 iterations.
  - edacc/ft/EdAcc600/output/ft_references.txt: EdAcc test set reference transcripts.
  - edacc/ft/EdAcc600/output/sclite/ft_results.txt: WER and results breakdown computed by SCLITE for EdAcc test set using Whisper fine-tuned on EdAcc dev set for 600 iterations.
  - edacc/ft/EdAcc600/edacc_test.ipynb: Produces EdAcc test set predicted transcripts using Whisper fine-tuned on EdAcc dev set for 600 iterations.

- edacc/zero_shot: Python files for running Whisper zero-shot and evaluation with EdAcc data and text files of reference data, predictions, and WER results.

  - edacc/zero_shot/output/sclite/dev_results.txt: WER and results breakdown computed by SCLITE for EdAcc dev set using Whisper zero-shot.
  - edacc/zero_shot/output/sclite/test_results.txt: WER and results breakdown computed by SCLITE for EdAcc test set using Whisper zero-shot.
  - edacc/zero_shot/output/dev_predictions.txt: EdAcc dev set transcripts predicted by Whisper zero-shot.
  - edacc/zero_shot/output/dev_references.txt: EdAcc dev set reference transcripts.
  - edacc/zero_shot/output/test_predictions.txt: EdAcc test set transcripts predicted by Whisper zero-shot.
  - edacc/zero_shot/output/test_references.txt: EdAcc test set reference transcripts.
  - edacc/zero_shot/edacc_zs_dev.ipynb: Runs Whisper zero-shot with EdAcc dev set and produces output. 
  - edacc/zero_shot/edacc_zs_test.ipynb: Runs Whisper zero-shot with EdAcc test set and produces output. 

- setup/environment.txt: All requirements for running data processing, zero-shot, and fine-tuning code.
- setup/sclite_setup.txt: All requirements for running SCLITE for evaluation. 

- ume_erj/data_processing: Python files for processing EdAcc data for use with Whisper.

  - ume_erj/data_processing/ume_erj_raw.ipynb: Standardizes and formats UME-ERJ data for evaluations with Whisper. Uploads data to HuggingFace.
  - ume_erj/data_processing/ume_erj_whisper.ipynb: Applies Whisper pre-processing to prepare UME-ERJ data for use in Whisper fine-tuning. Uploads data to HuggingFace.

- ume_erj/ft: Python files for running Whisper fine-tuning and evaluation with UME-ERJ data and text files of reference data, predictions, and WER results.

  - ume_erj/ft/ft_run/ume_erj_ft_test.ipynb: Runs fine-tuning with UME-ERJ train set for 3600 iterations tracking test set metrics. 
  - ume_erj/ft/ft_run/ume_erj_ft_val.ipynb:  Runs fine-tuning with UME-ERJ train set for 3600 iterations tracking validation set metrics. 
  - ume_erj/ft/output/sclite/ft_results.txt: WER and results breakdown computed by SCLITE for UME-ERJ test set using Whisper fine-tuned on UME-ERJ train set for 3600 iterations.
  - ume_erj/ft/output/ft_predictions.txt: UME-ERJ test set transcripts predicted by Whisper fine-tuned on UME-ERJ train set for 3600 iterations.
  - ume_erj/ft/output/ft_references.txt: UME-ERJ test set reference transcripts.
  - ume_erj/ft/ume_erj_test.ipynb: Produces UME-ERJ test set predicted transcripts using Whisper fine-tuned on UME-ERJ train set for 3600 iterations.

- ume_erj/zero_shot: Python files for running Whisper zero-shot and evaluation with UME-ERJ data and text files of reference data, predictions, and WER results.

  - ume_erj/zero_shot/output/sclite/dev_results.txt: WER and results breakdown computed by SCLITE for UME-ERJ train set using Whisper zero-shot.
  - ume_erj/zero_shot/output/sclite/test_results.txt: WER and results breakdown computed by SCLITE for UME-ERJ test set using Whisper zero-shot.
  - ume_erj/zero_shot/output/dev_predictions.txt: UME-ERJ train set transcripts predicted by Whisper zero-shot.
  - ume_erj/zero_shot/output/dev_references.txt: UME-ERJ train set reference transcripts.
  - ume_erj/zero_shot/output/test_predictions.txt: UME-ERJ test set transcripts predicted by Whisper zero-shot.
  - ume_erj/zero_shot/output/test_references.txt: UME-ERJ test set reference transcripts.
  - ume_erj/zero_shot/ume_erj_zs_test.ipynb: Runs Whisper zero-shot with UME-ERJ train set and produces output. 
  - ume_erj/zero_shot/ume_erj_zs_train.ipynb: Runs Whisper zero-shot with UME-ERJ test set and produces output. 
