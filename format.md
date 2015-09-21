# Data format

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

## Image data format
