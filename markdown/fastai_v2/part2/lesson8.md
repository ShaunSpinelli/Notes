# Lesson 8

## key point

- ipyhton debugger

- create rich conv structures

- batchnorm

part 1

transfer learning

overfitting - more data, data augmentation, generalizable arch, regularization, reduce arc complexity

embeddings 


data set dl 

```bash
    cd ~/fastai/courses/dl2
    ln -s ~/data data && cd $_
    mkdir pascal && cd $_
    curl -OL http://pjreddie.com/media/files/VOCtrainval_06-Nov-2007.tar
    curl -OL https://storage.googleapis.com/coco-dataset/external/PASCAL_VOC.zip
    tar -xf VOCtrainval_06-Nov-2007.tar
    unzip PASCAL_VOC.zip
    mv PASCAL_VOC/*.json .
    rmdir PASCAL_VOC

```