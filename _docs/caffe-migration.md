---
docid: caffe-migration
title: Upgrading to Caffe2
layout: docs
permalink: /docs/caffe-migration.html
---

## What's new in Caffe2?

One of basic units of computation in Caffe2 are the `Operators`. Each operator contains the logic necessary to compute the output given the appropriate number and types of inputs and parameters. The overall difference between operators' functionality in Caffe and Caffe2 is illustrated in the following graphic, respectively:

![operators comparison](../static/images/operators-comparison.png)

We've added a ton of operators to cover a wide range of functionality. You can browse the [Operator Catalogue](operators-catalogue.html), check out our amazing [Sparse Operations](sparse-operations.html), and learn how to write [custom operators](custom-operators.html).

## Caffe to Caffe2

### Converting from Caffe

Converting your models from original Caffe is relatively easy. We provide a tutorial below that will convert your caffemodel, but you will still need to verify that the accuracy and loss rates are within range or better.

#### Getting Caffe1 Models for Translation to Caffe2

Here you can find a tutorial with examples of downloading models from Caffe's original repository that you can use with the Caffe2 translator. Skip this if you're starting from scratch and just want to learn Caffe2.

[Browse](https://github.com/caffe2/caffe2/blob/gh-pages/tutorials/Getting_Caffe1_Models_for_Translation.ipynb) | [Download](../tutorials/Getting_Caffe1_Models_for_Translation.ipynb)

#### Converting Models from Caffe to Caffe2

A tutorial for converting your old Caffe models or for any of the models found in the Caffe Model Zoo is provided in the following Jupyter notebook found at `docs/tutorials/Caffe_translator.ipynb` or you can browse and download them here. Skip this if you're starting from scratch and just want to learn Caffe2.

[Browse](https://github.com/caffe2/caffe2/blob/gh-pages/tutorials/Caffe_translator.ipynb) | [Download](/tutorials/Caffe_translator.ipynb)

See the [tutorials][tutorial.html] page for prerequisites.

Alternatively you can try a command line python script tailor made for this purpose. It is found in Caffe2's [python folder](https://github.com/caffe2/caffe2/tree/master/caffe2/python).

* [caffe_translator.py](https://github.com/caffe2/caffe2/blob/master/caffe2/python/caffe_translator.py) - This script has built-in translators for common layers. The tutorial mentioned above implements this same script, so it may be helpful to review the tutorial to see how the script can be utilized. You can also call the script directly from command line.
* [caffe_translator_test.py](https://github.com/caffe2/caffe2/blob/master/caffe2/python/caffe_translator_test.py) - This a large test that goes through the translation of the BVLC caffenet model, runs an example through the whole model, and verifies numerically that all the results look right. In default, it is disabled unless you explicitly want to run it.

Usage is:

```
python -m caffe2.python.caffe_translator deploy.prototxt pretrained.caffemodel
```

## Torch to Caffe2

### How is Caffe2 different from PyTorch?

Caffe2 is built to excel at mobile and at large scale deployments. While it is new in Caffe2 to support multi-GPU, bringing Torch and Caffe2 together with the same level of GPU support, Caffe2 is built to excel at utilizing both single-host and multi-host GPUs. PyTorch is great for research, experimentation and trying out exotic neural networks, while Caffe2 is headed towards supporting more industrial-strength applications with a heavy focus on mobile. This is not to say that PyTorch doesn't do mobile or doesn't scale or that you can't use Caffe2 with some awesome new paradigm of neural network, we're just highlighting some of the current characteristics and directions for these two projects. We plan to have plenty of interoperability and methods of converting back and forth so you can experience the best of both worlds.

### Converting from Torch

This can currently be accomplished in a two step process where you convert to Caffe first and then to Caffe2 as described above.

[Github torch2caffe](https://github.com/facebook/fb-caffe-exts#torch2caffe)

## Troubleshooting

<TBD>