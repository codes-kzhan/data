

untar the data

```bash
tar -xvf ../../data/ILSVRC2012_img_train.tar -C train_tar
tar -xf ../../data/ILSVRC2012_img_val.tar -C val

ls train_tar/*.tar | xargs -I{} basename {} .tar | xargs -I{} mkdir -p train/{}
ls train_tar/*.tar | xargs -I{} basename {} .tar | xargs -I{} tar -xf train_tar/{}.tar -C train/{}
```

resize:

pack:

performance:

