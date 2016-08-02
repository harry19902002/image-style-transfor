# 照片风格转换

项目主要参考Anish Athalye的[Github项目][github]

该项目是基于TensorFlow进行的视频图像转化，参考[neural style][paper]这篇文章。

TensorFlow 并不支持 [L-BFGS][l-bfgs] (论文所用算法), 所以我们使用了 [Adam][adam]，这样可能需要用更多的参数来获得理想的转换图片.

TensorFlow 可能比其他的深度学习算法稍微[慢一些][tensorflow-benchmarks]。 
我想通过修改tensorFlow的实现方式，算法效率一定会再高一些。
现在，使用TensorFlow实现大概要比Torch工具慢3倍

## 如何运行

首先在根目录下下载[VGG-19网络模型][net]

并在项目根目录下键入：

`python neural_style.py --content 原始图片文件名 --styles 风格图片文件名 --out 生成图片文件名`


## 例子

使用 500-2000 迭代次数就可以有一个很不错的结果，通过修改其他参数我们可以得到不同的效果（比如--content-weight,--style-weight,and --learning-rate）。

这是一个迭代了1000次的例子(使用默认参数):

![output](examples/1-output.jpg)

原始图片:

![input-content](examples/1-content.jpg)

![input-style](examples/1-style.jpg)

## 环境需要

* TensorFlow
* SciPy
* Pillow
* NumPy
* [Pre-trained VGG network][net] (MD5 `8ee3263992981a1d26e73b3ca028a123`)

## License

Copyright (c) 2015-2016 Anish Athalye. Released under GPLv3. See
[LICENSE.txt][license] for details.

[net]: http://www.vlfeat.org/matconvnet/models/beta16/imagenet-vgg-verydeep-19.mat
[paper]: http://arxiv.org/pdf/1508.06576v2.pdf
[l-bfgs]: https://en.wikipedia.org/wiki/Limited-memory_BFGS
[adam]: http://arxiv.org/abs/1412.6980
[ad]: https://en.wikipedia.org/wiki/Automatic_differentiation
[tensorflow-benchmarks]: https://github.com/soumith/convnet-benchmarks
[license]: LICENSE.txt
[github]: https://github.com/anishathalye/neural-style
