PyTorch now officially supports GroupNormlization. I highly suggest using the groupnorm from PyTorch instead of this one.

## Updated  
  The code is updated accordinign to PyTorch v1.0rc1. 

# pytorch-groupnormalization
Pytorch implementation of group normalization in https://arxiv.org/abs/1803.08494 (Following the PyTorch Style)

This group normalization implementation is modified from the Instance Normalization in PyTorch. 

ImageNet Validation results. 


P.S. NCPG : Number Channels per Group. 

| Model         | NCPG |  Top1 Accuracy |  Top5 Accuracy | Link |
| ------------- |:----:|:------:|:------:|:----:|
| ResNet50      | 32   | 75.768% | 92.552% |[resnet50-groupnorm32](http://www.cs.unc.edu/~cyfu/resnet50_groupnorm32.tar)|
| ResNet50      | 16   | 75.872% | 92.780% |[resnet50-groupnorm16](http://www.cs.unc.edu/~cyfu/resnet50_groupnorm16.tar)|

 

Training Script : 
```script 
    python main.py IMAGENET_DIR --arch=resnet50 --group-norm=32 --epochs=100 --lr=0.1 --batch-size=256 --workers=8
```
Testing Script : 
```script 
    wget www.cs.unc.edu/~cyfu/resnet50_groupnorm32.tar
    python main.py IMAGENET_DIR --evaluate --batch-size=250 --arch=resnet50 --group-norm=32  --resume=./resnet50_groupnorm32.tar   
    
    wget www.cs.unc.edu/~cyfu/resnet50_groupnorm16.tar
    python main.py IMAGENET_DIR --evaluate --batch-size=250 --arch=resnet50 --group-norm=16  --resume=./resnet50_groupnorm16.tar   
```



Reference:

    @article{wu2018group,
      title={Group Normalization},
      author={Yuxin Wu, Kaiming He},
      journal={arXiv preprint arXiv:1803.08494},
      year={2018}
    }
