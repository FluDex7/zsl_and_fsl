# Zero-Shot & Few-Shot Learning

Материалы семинара по методам обучения без данных и с минимальной разметкой (Zero-Shot Learning, Few-Shot Learning) для магистрантов и аспирантов.

Покрывает Computer Vision и NLP: от атрибутных моделей Lampert (2009) до CLIP, OWL-ViT, Prototypical Networks, MAML, SetFit и LoRA.

---

## Структура репозитория

```
zsl_and_fsl/
├── ZSL_FSL_Presentation.pptx    # Презентация (Часть I + Часть II)
├── ZSL_FSL_text.md              # Полный учебный гайд (конспект)
├── JupiterNoteBooks/            # Jupyter-ноутбуки для демо
│   ├── ZSL_FSL_CV_Demo.ipynb    # Демо для CV (CLIP, OWL-ViT, ProtoNet)
│   └── ZSL_FSL_Seminar_Demo.ipynb  # Демо для NLP (BART-MNLI, SetFit, ProtoNet)
└── README.md
```

---

## Содержание

### Презентация

**Часть I — Фундамент + Zero-Shot Learning:**
- Что такое ZSL/FSL, формальная постановка, GZSL
- История: Fei-Fei (2006) → Lampert DAP (2009) → DeViSE → f-CLSWGAN → CLIP
- DAP — интуиция (пример с зеброй) + математика
- CLIP — архитектура (ViT + Text Transformer), контрастивный loss, zero-shot инференс
- SigLIP — sigmoid vs softmax
- OWL-ViT — zero-shot object detection
- NLI-подход к ZSL в NLP (BART-MNLI, DeBERTa-v3)
- GPT-3 и In-Context Learning

**Часть II — Few-Shot Learning:**
- Siamese Networks, Matching Networks
- Prototypical Networks — математика + связь с дивергенциями Брэгмана
- Relation Networks
- MAML (inner/outer loop), Reptile
- CLIP как few-shot learner (CoOp, Tip-Adapter)
- SetFit, PET
- LoRA, Adapters, Prefix Tuning
- Сводная таблица всех методов, практические рекомендации
- Связь ZSL/FSL с другими областями ML

### Учебный гайд (`ZSL_FSL_text.md`)

Полный разбор всех тем из презентации с объяснениями, формулами (с расшифровкой каждой переменной), интуицией и примерами. Две части:
- Часть I: фундамент, история, ZSL в CV (DAP, embedding, f-CLSWGAN, CLIP, SigLIP, OWL-ViT), ZSL в NLP
- Часть II: FSL в CV (Siamese, Matching, ProtoNet, Relation, MAML, Reptile), FSL в NLP (SetFit, PET, ICL, LoRA/Adapters/Prefix), сводка, связи с другими областями

### Jupyter-ноутбуки

**CV Demo** (`ZSL_FSL_CV_Demo.ipynb`):
- Zero-shot image classification через CLIP (классификация по произвольным текстовым меткам, 4 «оси» классификации, prompt engineering)
- Zero-shot object detection через OWL-ViT (bounding boxes по текстовым запросам)
- Few-shot: Prototypical Networks на CIFAR-100 (5-way 5-shot, сравнение с CLIP zero-shot)
- t-SNE визуализация CLIP-эмбеддингов

**NLP Demo** (`ZSL_FSL_Seminar_Demo.ipynb`):
- Zero-shot text classification через BART-MNLI на AG News
- Few-shot через SetFit (K=8 примеров на класс)
- Prototypical Networks на текстовых эмбеддингах
- Эксперимент с K=2,4,8,16 — когда few-shot обгоняет zero-shot
- Confusion matrices, сравнительные таблицы

---

## Как запустить

### Ноутбуки

Откройте в Google Colab (рекомендуется GPU runtime — T4):

```
Colab → File → Upload Notebook → выберите .ipynb
Runtime → Change runtime type → T4 GPU
```

Или через VSCode + Google Colab Extension.

Зависимости устанавливаются в первой ячейке ноутбука:
```bash
pip install transformers torch torchvision datasets scikit-learn matplotlib
```

Для NLP Demo дополнительно:
```bash
pip install setfit
```

> Если SetFit не импортируется из-за несовместимости с transformers:
> ```bash
> pip install --no-cache-dir "setfit @ git+https://github.com/huggingface/setfit.git@main"
> ```
> и перезапустите ядро.

---

## Ключевые источники

| # | Статья | Конференция |
|---|--------|-------------|
| 1 | Lampert et al. — DAP/IAP | CVPR 2009 / TPAMI 2014 |
| 2 | Snell et al. — Prototypical Networks | NeurIPS 2017 |
| 3 | Finn et al. — MAML | ICML 2017 |
| 4 | Xian et al. — f-CLSWGAN | CVPR 2018 |
| 5 | Radford et al. — CLIP | ICML 2021 |
| 6 | Minderer et al. — OWL-ViT | ECCV 2022 |
| 7 | Tunstall et al. — SetFit | arXiv 2022 |
| 8 | Zhai et al. — SigLIP | arXiv 2023 |
| 9 | Hu et al. — LoRA | ICLR 2022 |
| 10 | Brown et al. — GPT-3 / ICL | NeurIPS 2020 |

Полный список из 32 статей — в учебном гайде (Приложение B).
