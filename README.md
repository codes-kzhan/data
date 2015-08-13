# Datasets

A collection of "big" datasets converted to an uniform format. The copyrights
these datasets belong to the original authors.

## Text classification

Summary of the datasets.

| name | #class | +1/-1 |  #training | #testing | #feature |
| ---  | ----  | --- | --- | --- | --- | --- |
| [CriteoI](#criteoi) | 2 | ? | 45,840,617 | 6,042,135 | ? |
| [CriteoII](#criteoii) | 2 | ? | ~ 2,000,000,000 | ? | ~ 800,000,000 |
| Avito |
| Avazu |
| CTRIa |
| CTRII |
| CTRIII |
| KDD2010a | 2 |
| KDD2010b | 2 |

## Text data format

We use a text format is compatible with the
[LIBSVM](https://www.csie.ntu.edu.tw/~cjlin/libsvm/) format. Each example is stored as
a line of text in the following format:

```
label index[:value] index[:value] ... index[:value]
```
- `label`: +1 or -1 for binary class. 0, 1, 3 ... for multi-class, and a float
  for regression.
- `index`: the unsigned 64-bit integer feature index. The leading 10-bit is preserved for indicating which feature group this
  feature belongs to, while the rest bits are for the feature ID. For example,
  assume there is a feature group called `USER_NAME`, then the feature
  presenting `alex smola` can be indexed by
  ```
  (hash64("USER_NAME") << 54) | (hash64("alex smola) >> 10)
  ```
- `value`: the according float weight of this feature. It can be omitted if all
  values are ones, which is common when using the one-hot encoding.

## CriteoI

[Criteo Kaggle CTR competition](https://www.kaggle.com/c/criteo-display-ad-challenge/)
