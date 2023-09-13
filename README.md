# Understanding Vision Transformers through Attention Analysis

This repository explores various methods for analyzing attention patterns in Vision Transformers (ViTs). Understanding how ViTs distribute their attention can provide valuable insights into how they process visual information. We delve into three methods for attention analysis: Mean Attention Distance, Attention Rollout, and Attention Heatmaps.

## Installation

To use the tools and scripts in this repository, follow these installation instructions:

1. To run on Google Colab, we need to update the gdown library like so:

   ```bash
   pip install -U gdown -q
   ```

## Method I: Mean Attention Distance

Dosovitskiy et al. and Raghu et al. employ a measure known as "mean attention distance" to gain insights into how local and global information flow through different Transformer blocks in ViTs.

### Definition
Mean attention distance is defined as the distance between query tokens and other tokens, weighted by attention scores. The process involves:
1. Extracting individual patches (tokens) from an image.
2. Calculating the geometric distance between these tokens.
3. Multiplying the distances by the corresponding attention scores.

This method allows us to understand how attention is distributed within the network after forwarding an image during inference.

## Method II: Attention Rollout

Abnar et al. introduce "Attention Rollout" as a technique for quantifying how information flows through the self-attention layers of Transformer blocks. This method has been used by the original ViT authors to investigate learned representations.

### Approach
In this method, we:
- Average attention weights across all heads in ViT layers.
- Recursively multiply the weight matrices of all layers, capturing the mixing of attention across tokens through all layers.

## Method III: Attention Heatmaps

A simple yet effective way to gain insights into ViT representations is by visualizing attention maps overlaid on input images. This method is particularly useful for understanding what the model attends to within an image.

### Visualization
We utilize the DINO model, known for producing high-quality attention heatmaps. Each Transformer block in ViT consists of multiple heads, with each head projecting input data into different sub-spaces. Visualizing attention head maps separately allows us to understand what each head focuses on.

## References

- Dosovitskiy, A. et al. (2021). An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale. [arXiv:2010.11929](https://arxiv.org/abs/2010.11929).
- Raghu, M. et al. (2021). Understanding the Difficulty of Training Transformers. [arXiv:2101.06174](https://arxiv.org/abs/2101.06174).
- Abnar, S. et al. (2021). Quantifying Attention Flow in Transformers. [arXiv:2102.05202](https://arxiv.org/abs/2102.05202).

