# Deep Learning Project 2: Handwritten letters with a GAN

In this project we make a **GAN** (Generative Adversarial Network) that draws handwritten letters.
We use the **EMNIST Letters** dataset (28x28 grey images, letters A to Z).

## Goals

| Part | What the model does | Status |
|---|---|---|
| Data | Load and prepare the images | In progress |
| Basic GAN | Makes random letters | Not started |
| Conditional GAN | Makes the letter that the user chooses | Not started |
| One-shot GAN | Makes a new letter from only one example | Not started |

## Files

| File | What is inside |
|---|---|
| `gan.ipynb` | Code, results and explanations |
| `PLAN.md` | Our team plan (in Turkish) |

## How to run

1. Install Python 3.10.
2. Install PyTorch. With an NVIDIA GPU:
   ```
   pip install torch torchvision --index-url https://download.pytorch.org/whl/cu126
   ```
   Without a GPU:
   ```
   pip install torch torchvision
   ```
3. Install the other tools:
   ```
   pip install matplotlib ipykernel
   ```
4. Open `gan.ipynb` and click **Run All**.

The data downloads to the `data/` folder the first time. It is large, so it is not in the repository.

## Team

| Name | Student ID |
|---|---|
| | |
| | |
