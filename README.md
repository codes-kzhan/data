# Datasets

A collection of datasets converted to an uniform format. The copyrights
belong to the original authors.

## Text classification

Summary of the datasets.

| name | class | +1/-1 |  training | testing | feature | feature group |
| ---  | ----  | --- | --- | --- | --- | --- | --- |
| [CriteoKaggle](#criteo-kaggle) | 2 | 3.9:1 | 45,840,617 | 6,042,135 | 34,291K | 39 |
| [CriteoTera](#criteo-tera) | 2 | ? | ~2B | - | ~800M | 39 |
| [CTRa](#ctra) | 2 | 1:1 | 223,836 | 62,549 | 13,141K | ~200 |
| [CTRb](#ctrb) | 2 | 8.6:1 | 164,507 | 47,716 | 17,417K | ~100 |
| Avito |
| Avazu |

## Text data format

We use a text format compatible with the
[LIBSVM](https://www.csie.ntu.edu.tw/~cjlin/libsvm/) format. Each example is stored as
a line of text in the following format:

```
label index[:value] index[:value] ... index[:value]
```
- `label`: label for the example
  - an integer starting from 0 for classification
  - a float for regression.
- `index`: an unsigned 64-bit integer feature index.
  - The leading 10 bits are preserved for indicating which feature group this
  feature belongs to
  - The last 54 bits  are for the feature ID.

  For example, assume there is a feature group called `USER_NAME`, then the feature
  presenting `mu li` can be indexed by

  ```
  (hash64("USER_NAME") << 54) | (hash64("mu li") >> 10)
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

Ads CTR dataset from
[Criteo Kaggle CTR competition](https://www.kaggle.com/c/criteo-display-ad-challenge/).

Convert the data from the original format:

```bash
wget https://s3-eu-west-1.amazonaws.com/criteo-labs/dac.tar.gz
tar -zxvf dac.tar.gz
wormhole/bin/convert.dmlc -data_in train.txt -format_in criteo -data_out criteo_kaggle_train -format_out libsvm
wormhole/bin/convert.dmlc -data_in test.txt -format_in criteo_test -data_out criteo_kaggle_test -format_out libsvm
```

A converted version is provided.

| filename | size | download | md5sum |
| ---  | --- | --- | --- |
| criteo_kaggle.7z | 3.2GB | [box.com](https://cmu.box.com/shared/static/njfxkocme39wae7rl59rstnaxedufwyi.7z) | `cf0494f020419561ea947194f6b5f6a4` |


Node: all labels in the test dataset are 0.


## Criteo Tera

A larger version of Criteo Kaggle, one can download and convert them by

```bash
for i in {0..23}; do
    curl http://azuremlsampleexperiments.blob.core.windows.net/criteo/day_${i}.gz | \
        gzip -d | wormhole/bin/convert.dmlc -data_in stdin -format_in criteo \
        -data_out day_${i} -format_out libsvm
done
```

## CTRa

Ads CTR dataset from an anonymous Internet company. Negative examples are down
sampled.


| filename | size | download | md5sum |
| ---  | --- | --- | --- |
| ctra.7z | 200MB | [box.com](https://cmu.box.com/shared/static/s8wjtptm5qlhe487tqfz0aftljiisp0k.7z) [pan.baidu.com](http://pan.baidu.com/s/1mGiFs) | `3b6c8ca1070b09d4673d30b0006e0f1c` |

## CTRb

Ads CTR dataset from an anonymous Internet company.

| filename | size | download | md5sum |
| ---  | --- | --- | --- |
| ctrb.7z | 370MB | [box.com](https://cmu.box.com/shared/static/grvidn3k0uc9qburz9s7bupwidzwjlj6.7z) [pan.baidu.com](http://pan.baidu.com/s/1jGEkiPo) | `7878b9ba2d663f321ce79304f9920421` |
