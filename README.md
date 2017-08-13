# Reproduction of Focal-loss on Caffe

**I didn't implement CPU version. If you want to see the details, please check `focal_loss_layer.cu`**

To use [Focal-Loss](https://arxiv.org/abs/1708.02002) layer, you can:

1) Directly compile my [CaffeMex_v2](https://github.com/sciencefans/CaffeMex_v2) on Linux or Windows, the layer is already embedded. 

2) You can also add the three files, `focal_loss_layer.cpp`, `focal_loss_layer.cu` and `focal_loss_layer.hpp`, and modify `caffe.proto` in your own caffe. 

## An example in prototxt

```
layer {
  name: "loss_focal"
  type: "FocalLoss"
  bottom: "predicted"
  bottom: "label"
  top: "loss_focal"
  loss_weight: 10
  loss_param{
    normalize: true
    normalization: FULL
  } 
}
```