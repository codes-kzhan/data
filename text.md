# Text classification

## Criteo Kaggle

Ads CTR dataset from
[Criteo Kaggle CTR competition](https://www.kaggle.com/c/criteo-display-ad-challenge/). Provided
by

Convert the data from the original format:

```bash
wget https://s3-eu-west-1.amazonaws.com/criteo-labs/dac.tar.gz
tar -zxvf dac.tar.gz
wormhole/bin/convert.dmlc -data_in train.txt -format_in criteo -data_out criteo_kaggle_train -format_out libsvm
wormhole/bin/convert.dmlc -data_in test.txt -format_in criteo_test -data_out criteo_kaggle_test -format_out libsvm
```

A converted version is provided.

| filename | size | md5sum | download |
| ---  | --- | --- | --- |
| criteo_kaggle.7z | 3.2GB | `cf0494f020419561ea947194f6b5f6a4` | [box.com](https://cmu.box.com/shared/static/njfxkocme39wae7rl59rstnaxedufwyi.7z) |


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


| filename | size | md5sum | download |
| ---  | --- | --- | --- |
| ctra.7z | 200MB | `3b6c8ca1070b09d4673d30b0006e0f1c` | [box.com](https://cmu.box.com/shared/static/s8wjtptm5qlhe487tqfz0aftljiisp0k.7z), [pan.baidu.com](http://pan.baidu.com/s/1mGiFs)|

## CTRb

Ads CTR dataset from an anonymous Internet company.

| filename | size | md5sum | download |
| ---  | --- | --- | --- |
| ctrb.7z | 370MB | `7878b9ba2d663f321ce79304f9920421` | [box.com](https://cmu.box.com/shared/static/grvidn3k0uc9qburz9s7bupwidzwjlj6.7z), [pan.baidu.com](http://pan.baidu.com/s/1jGEkiPo) |
