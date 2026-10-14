# ASL Alphabet Recognition: Internal vs External Generalisation

DATAX504 final project. This project tests whether a model that scores very
high on one ASL alphabet dataset still works on new images from a different source.

## What is in this folder
- `asl_alphabet_final.ipynb`: the full notebook (data split, three models,
  internal and external evaluation, error analysis). Outputs are included.

## Models
- M0: CNN trained from scratch (baseline)
- M1: MobileNetV2 (ImageNet pretrained, frozen) with a new classification head
- M2: M1 plus data augmentation

## Data (both on Kaggle)
- Main dataset: ASL Alphabet, Akash Nagaraj, 2018 (87,000 images, 29 classes)
  https://www.kaggle.com/datasets/grassknoted/asl-alphabet
- External test set: ASL Alphabet Test, danrasband (870 images, 30 per class)
  https://www.kaggle.com/datasets/danrasband/asl-alphabet-test

## How to reproduce
1. Create a new Kaggle notebook and upload `asl_alphabet_final.ipynb`.
2. Add both datasets above as inputs (Add Input).
3. Turn on a GPU (Settings, Accelerator).
4. Run all cells from top to bottom.

Paths used in the notebook:
- /kaggle/input/datasets/grassknoted/asl-alphabet/asl_alphabet_train/asl_alphabet_train
- /kaggle/input/datasets/danrasband/asl-alphabet-test

## Settings
TensorFlow 2.20.0, image size 128x128, batch size 32, seed 42, Adam (learning rate 0.001),
early stopping on validation loss (patience 3), maximum 15 epochs, stratified 80/10/10 split.

## Main results (Macro-F1)
| Model | Internal | External |
|---|---|---|
| M0 CNN | 99.84% | 18.50% |
| M1 MobileNetV2 | 99.68% | 26.15% |
| M2 MobileNetV2 + augmentation | 95.87% | 27.14% |

## AI use
See Section 9 of the report for the full disclosure.
