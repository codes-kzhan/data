# Datasets

A collection of "big" datasets converted to an uniform format. The copyrights
these datasets belong to the original authors.

## Text classification

Summary of the datasets.

| name | class | +1/-1 |  training | testing | feature | feature group |
| ---  | ----  | --- | --- | --- | --- | --- | --- |
| [CriteoKaggle](#criteokaggle) | 2 | ? | 45,840,617 | 6,042,135 | ? | 39 |
| [CriteoTera](#criteoii) | 2 | ? | ~ 2,000,000,000 | ? | ~ 800,000,000 | 39 |
| Avito |
| Avazu |
| [CTRa](#ctra) | 1:1 | | | | |
| CTRb |
| CTRc |

## Text data format

We use a text format compatible with the
[LIBSVM](https://www.csie.ntu.edu.tw/~cjlin/libsvm/) format. Each example is stored as
a line of text in the following format:

```
label index[:value] index[:value] ... index[:value]
```
- `label`: label for the example
  - 0, 1, 2, ... for multi-class
  - a float for regression.
- `index`: the unsigned 64-bit integer feature index.
  - The leading 10 bits are preserved for indicating which feature group this
  feature belongs to
  - The last 54 bits  are for the feature ID.

  For example, assume there is a feature group called `USER_NAME`, then the feature
  presenting `alex smola` can be indexed by

  ```
  (hash64("USER_NAME") << 54) | (hash64("alex smola) >> 10)
  ```
- `value`: the according float weight of this feature. It can be omitted if all
  values are ones, which is common when using the one-hot encoding.

[wormhole](https://github.com/dmlc/wormhole/) provides tool `convert.dmlc` to
convert datasets with different formats.

```
git clone https://github.com/dmlc/wormhole
cd wormhole && make deps -j4 && make tool
```

## Criteo Kaggle

Ad ads CTR dataset from
[Criteo Kaggle CTR competition](https://www.kaggle.com/c/criteo-display-ad-challenge/)

```bash
wget https://s3-eu-west-1.amazonaws.com/criteo-labs/dac.tar.gz
tar -zxvf dac.tar.gz
wormhole/bin/convert.dmlc -data_in train.txt -format_in criteo -data_out criteo_kaggle_train -format_out libsvm
wormhole/bin/convert.dmlc -data_in test.txt -format_in criteo_test -data_out criteo_kaggle_test -format_out libsvm
```

## CTRa

An ads CTR dataset from an anonymous Internet company.

[ctra.7z 200MB](http://www.cs.cmu.edu/~muli/data/ctra.7z) md5: 3b6c8ca1070b09d4673d30b0006e0f1c

## CTRb

An ads CTR dataset from an anonymous Internet company.
