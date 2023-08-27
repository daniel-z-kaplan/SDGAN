# SDGAN
 SDGAN: Tuning Stable Diffusion with an adversarial network

This is a research project aimed at enhancing Stable Diffusion with GAN training for better perceptual detail. Currently, no pretrained model weights are available. Things are still in flux and the model may change in ways that are not backwards compatible with trained weights. Use at your own risk.

TODO
* ☐ Investigate using different samples for generator and discriminator training
* ☑ ~~Test the effect of adding self-attention to all layers~~ Failed due to CUDA running out of memory
* ☐ Test the effect of different parameter initializations
* ☑ Investigate using cross attention

BIBLIOGRAPHY (incomplete)
* [High-Resolution Image Synthesis with Latent Diffusion Models](https://arxiv.org/abs/2112.10752)
* [Image-to-Image Translation with Conditional Adversarial Networks](https://arxiv.org/abs/1611.07004)
* [Diffusion-GAN: Training GANs with Diffusion](https://arxiv.org/abs/2206.02262)
* [Scaling up GANs for Text-to-Image Synthesis](https://arxiv.org/abs/2303.05511)
* [Fast Transformer Decoding: One Write-Head is All You Need](https://arxiv.org/abs/1911.02150)
* [Tackling the Generative Learning Trilemma with Denoising Diffusion GANs](https://arxiv.org/abs/2112.07804)
* [Refining Generative Process with Discriminator Guidance in Score-based Diffusion Models](https://arxiv.org/abs/2211.17091)
* [Refining activation downsampling with SoftPool](https://arxiv.org/abs/2101.00440)
* [Adversarial score matching and improved sampling for image generation](https://arxiv.org/abs/2009.05475)


### LDM Stuff


https://github.com/CompVis/latent-diffusion/tree/main
Download above repository.
Create conda env as specified.
Downgrade torchmetrics to 0.5.0.
Upgrade torch to most recent version.


Need to run both download scripts in LDM repo.
```bash scripts/download_first_stages.sh```
```bash scripts/download_models.sh```


There are three files to wget.
```https://huggingface.co/datasets/KublaiKhan1/CelebA-HQ/resolve/main/P1.zip```
```https://huggingface.co/datasets/KublaiKhan1/CelebA-HQ/resolve/main/P2.zip```
```https://huggingface.co/datasets/KublaiKhan1/CelebA-HQ/resolve/main/P3.zip```

Unzip them.
The contents of those folders goes into latent-diffusion/data/celebahq. 
There should be 30k files there after this step.


In latent-diffusion/data, put the celebahq train & val txt from src/taming-transformers/data


Model gets copied into latent-diffusion/models/ldm/celeba256/checkpoints, and renamed last.ckpt

This is what I run, might not work in JEWELS.
```python3 main.py --base configs/latent-diffusion/celebahq-ldm-vq-4.yaml -t --resume models/ldm/celeba256/ --gpus=0,```

Things to note while running this.
If you get errors regarding NPY files, just rerun.
If you get other errors, try rerunning again.






##


For celeba:
https://drive.google.com/drive/folders/0B4qLcYyJmiz0TXY1NG02bzZVRGs?resourcekey=0-arAVTUfW9KRhN-irJchVKQ
https://drive.google.com/drive/folders/0B7EVK8r0v71pWEZsZE9oNnFzTm8?resourcekey=0-5BR16BdXnb8hVj6CNHKzLg
