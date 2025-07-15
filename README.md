# A Guide to Downloading ImageNet Dataset on Linux

[ImageNet](https://www.image-net.org)

## Download ImageNet

```bash
mkdir ImageNet
cd ImageNet
```

Download the training set.

```bash
wget -c https://image-net.org/data/ILSVRC/2012/ILSVRC2012_img_train.tar --no-check-certificate
```

Download the validation set.

```bash
wget -c https://image-net.org/data/ILSVRC/2012/ILSVRC2012_img_val.tar --no-check-certificate
```

Download the development kit.

```bash
wget https://image-net.org/data/ILSVRC/2012/ILSVRC2012_devkit_t12.tar.gz --no-check-certificate
```

## Unpack

### Training set

```bash
mkdir train
tar -xvf ILSVRC2012_img_train.tar -C train && for x in `ls train/*tar`; do fn=train/`basename $x .tar`; mkdir $fn; tar -xvf $x -C $fn; rm -f $fn.tar; done
```

```bash
cd train
ls -lR|grep "^d"|wc -l
# 1000
ls -lR|grep "^-"|wc -l
# 1281167
```

### Validation set

```bash
# back to /path/to/ImageNet
mkdir val
tar xvf ILSVRC2012_img_val.tar -C ./val
tar -xzf ILSVRC2012_devkit_t12.tar.gz
```

```bash
python unzip.py
```

```bash
cd val
ls -lR|grep "^d"|wc -l
# 1000
ls -lR|grep "^-"|wc -l
# 50000
```

## Acknowledgments

[linux下载/解压ImageNet-1k数据集](https://blog.csdn.net/qq_45588019/article/details/125642466)
