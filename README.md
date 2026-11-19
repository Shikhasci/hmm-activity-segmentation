# hmm-activity-segmentation

# HMM Activity Segmentation

Unsupervised segmentation of human activities from smartphone accelerometer and gyroscope data, using Gaussian hidden Markov models. Final project for CS275P (Probabilistic Models / generative models).

**Team:** Shikha Patel, Thomas-Evans Barton, Sakshi Nikte, Rohan Ganesh

## Problem

Given windowed smartphone sensor features, infer the sequence of latent activity states without using activity labels during training. Labels are used only to evaluate the learned states.

## Dataset

UCI Human Activity Recognition Using Smartphones (30 subjects, six activities: walking, walking upstairs, walking downstairs, sitting, standing, laying).

Download: https://archive.ics.uci.edu/dataset/240/human+activity+recognition+using+smartphones

Unzip the download so the folder structure looks like this:

```
UCI HAR Dataset/
  train/
    X_train.txt
    y_train.txt
    subject_train.txt
  test/
    ...
```

The dataset is not included in this repository. Set the path to the dataset at the top of the notebook (`ROOT`).

## Setup

```bash
pip install -r requirements.txt
jupyter notebook hmm_activity_segmentation.ipynb
```

## Current status

- [x] Non-temporal baselines: k-means (ARI = 0.42) and diagonal-covariance GMM (ARI = 0.25) on the training split
- [ ] Discrete HMM: forward-backward and Viterbi, checked on synthetic data
- [ ] Gaussian HMM: Baum-Welch (EM), with log-likelihood tracking
- [ ] Evaluation on held-out subjects (Viterbi accuracy after Hungarian matching, ARI, confusion matrix)
- [ ] Final report figures

## Repository contents

| File | Description |
|---|---|
| `hmm_activity_segmentation.ipynb` | Data loading, baselines, and (in progress) HMM implementation |
| `figures/prelim_pca.pdf` | Preliminary figure: PCA projection of true labels vs. k-means clusters |
| `requirements.txt` | Python dependencies |

## Implementation notes

All HMM algorithms (forward-backward, Viterbi, Baum-Welch) are implemented from scratch in the notebook. No HMM library is used for the learning procedure.

## References

- Rabiner, L. R. (1989). A tutorial on hidden Markov models and selected applications in speech recognition. *Proceedings of the IEEE.*
- Ghahramani, Z. (2001). An introduction to hidden Markov models and Bayesian networks. *International Journal of Pattern Recognition and Artificial Intelligence.*
- Anguita, D., et al. (2013). A public domain dataset for human activity recognition using smartphones. *ESANN.*
