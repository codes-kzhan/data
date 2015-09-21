# Datasets

A personal collection of datasets converted to uniformed formats. They can be
used directly by most [DMLC projects](http://dmlc.ml/). The copyrights of these datasets
belong to the original authors.

## Text classification

All are converted into the [LIBSVM format](format.md#text-data-format).

| name | class | +1/-1 |  training | testing | feature | feature group |
| ---  | ----  | --- | --- | --- | --- | --- | --- |
| [CriteoKaggle](text.md#criteo-kaggle) | 2 | 3.9:1 | 4.584 × 10<sup>7</sup> K | 6,042 K |
| 34,291 K | 39 |
| [CriteoTera](text.md#criteo-tera) | 2 | ? | ~2 B | - | ~800 M | 39 |
| [CTRa](text.md#ctra) | 2 | 1:1 | 223,836 | 63,549 | 13,141 K | ~200 |
| [CTRb](text.md#ctrb) | 2 | 8.6:1 | 164,507 | 47,716 | 17,417K | ~100 |
| Avito |
| Avazu |

## Image classification

All are converted into the [recordio format](format.md#image-data-format)

| name | class | image size | training | testing |
| ---- | ----- | ---------- | -------- | ------- |
| [CIFAR10](image.md#cifar-10) | 10 |
