# Datasets

A personal collection of datasets converted to uniformed formats. They can be
used directly by most [DMLC projects](http://dmlc.ml/). The copyrights of these datasets
belong to the original authors.

## Text classification

All are converted into the [LIBSVM format](format.md#text-data-format).

| name | class | +1/-1 |  training | testing | feature | feature group |
| ---  | ----  | --- | --- | --- | --- | --- | --- |
| [CriteoKaggle](text.md#criteo-kaggle) | 2 | 3.9:1 | 4.584 × 10<sup>7</sup> | 6.042 × 10<sup>6</sup> | 3.429 × 10<sup>7</sup>K | 39 |
| [CriteoTera](text.md#criteo-tera) | 2 | ? | 2 × 10<sup>9</sup>B | - | 8 × 10<sup>8</sup> M | 39 |
| [CTRa](text.md#ctra) | 2 | 1:1 | 2.238 × 10<sup>5</sup> | 6.355 × 10<sup>4</sup> | 1.314 × 10<sup>7</sup> | ~200 |
| [CTRb](text.md#ctrb) | 2 | 8.6:1 | 1.645 × 10<sup>5</sup> | 4.772 × 10<sup>4</sup> | 1.742 × 10<sup>7</sup> | ~100 |
| Avito |
| Avazu |

## Image classification

All are converted into the [recordio format](format.md#image-data-format)

| name | class | image size | training | testing |
| ---- | ----- | ---------- | -------- | ------- |
| [CIFAR10](image.md#cifar-10) | 10 | 28 × 28 × 3 | 60,000 | 10,000 |
