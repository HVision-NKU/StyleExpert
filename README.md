# StyleExpert

> **Mixture of Style Experts for Diverse Image Stylization**

<a href="https://arxiv.org/abs/2511.20614"><img src="[https://img.shields.io/badge/arXiv-StyleExpert-red](https://www.google.com/search?q=https://img.shields.io/badge/arXiv-StyleExpert-red)" alt="arXiv"></a>
<a href="https://hh-lg.github.io/StyleExpert-Page/"><img src="[https://img.shields.io/badge/Project%20Page-StyleExpert-blue](https://www.google.com/search?q=https://img.shields.io/badge/Project%2520Page-StyleExpert-blue)" alt="Project Page"></a>
<a href="https://huggingface.co/HH-LG/StyleExpert"><img src="[https://img.shields.io/badge/](https://img.shields.io/badge/)🤗_HuggingFace-Model-ffbd45.svg" alt="HuggingFace Model"></a>
<a href="https://huggingface.co/datasets/HH-LG/StyleExpert"><img src="[https://img.shields.io/badge/](https://img.shields.io/badge/)🤗_HuggingFace-Dataset-ffbd45.svg" alt="HuggingFace Dataset"></a>

<img src='./figures/teaser.png' width='100%' />

## 🖼️ Visual Results

<img src='./figures/compare.png' width='100%' />

## 🔧 Dependencies and Installation

We recommend using **Python 3.10** and **PyTorch** with CUDA support. To set up the environment:

```bash
# Create a new conda environment
conda create -n styleexpert python=3.10
conda activate styleexpert

# Install requirements
pip install -r requirements.txt

```

## ⚡ Quick Inference

### Tips

StyleExpert uses a **Mixture of Experts (MoE)** architecture. For the best results on complex semantic styles (like specific brushstrokes or materials), ensure your style reference image clearly showcases those textures. The model uses a pre-trained **Style Representation Encoder** to guide the router.

### Local Gradio Demo

```bash
python app.py

```
### Model Download

You can download the base model **FLUX.1-Kontext-dev** and our **StyleExpert** adapters directly from Hugging Face:

* **Base Model:** [FLUX.1-Kontext-dev](https://huggingface.co/black-forest-labs/FLUX.1-Kontext-dev)
* **StyleExpert LoRA Experts:** [Hugging Face Link](https://www.google.com/search?q=https://huggingface.co/shihao/StyleExpert)

Alternatively, use the provided script:

```bash
bash download_models.sh --token YOUR_HF_TOKEN

```

This will download these fixed repos into the local default paths used by inference:

* `HH-LG/StyleExpert` -> `./weights/`
* `black-forest-labs/FLUX.1-Kontext-dev` -> `./models/FLUX.1-Kontext-dev/`
* `google/siglip-so400m-patch14-384` -> `./models/siglip-so400m-patch14-384/`

---

## 📊 Dataset: StyleExpert-500K

We provide the **StyleExpert-500K** dataset, containing 500,000 high-quality content-style-stylized triplets. This dataset is specifically curated to balance color-centric and semantic-centric styles.

### Download via Script:

```bash
python download_dataset.py --token YOUR_HF_TOKEN

# only fetch metadata first
python download_dataset.py --metadata-only --token YOUR_HF_TOKEN

# or
bash download_dataset.sh --token YOUR_HF_TOKEN
```


### Single Case Inference

```bash
python infer.py --content_path ./data/content.jpg --style_path ./data/style.jpg

```

---
## 🧪 Method Overview

StyleExpert utilizes a two-stage training approach:

1. **Style Representation Encoder:** Trained with **InfoNCE loss**  to learn discriminative style features.
2. **MoE Fine-tuning:** Uses a similarity-aware gating mechanism to route styles to specialized LoRA experts.

---

## 📜 Citation

If **StyleExpert** helps your research, please star the repo and cite our work:

```bibtex
@article{zhu2026styleexpert,
  title={Mixture of Style Experts for Diverse Image Stylization},
  author={Zhu, Shihao and Ouyang, Ziheng and Kang, Yijia and Wang, Qilong and Zhou, Mi and Li, Bo and Cheng, Ming-Ming and Hou, Qibin},
  journal={CVPR},
  year={2026}
}

```

## 📧 Contact

For questions, please open an issue or contact [Shihao Zhu](zhushihao@mail.nankai.edu.cn).

## License

Licensed under [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/) for non-commercial use.
