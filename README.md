# LightLDA

LightLDA is a distributed system for large scale topic modeling. It implements a distributed sampler that enables very large data sizes and models. LightLDA improves sampling throughput and convergence speed via a fast O(1) metropolis-Hastings algorithm, and allows small cluster to tackle very large data and model sizes through model scheduling and data parallelism architecture. LightLDA is implemented with C++ for performance consideration.

We have sucessfully trained big topic models (with trillions of parameters) on big data (Top 10% PageRank values of Bing indexed page, containing billions of documents) in Microsoft. For more technical details, please refer to our [WWW'15 paper](http://www.www2015.it/documents/proceedings/proceedings/p1351.pdf). 

For documents, please view our website [http://www.dmtk.io](http://www.dmtk.io).

## Why LightLDA

The highlight features of LightLDA are

* **Scalable**: LightLDA can train models with trillions of parameters on big data with billions of documents, a scale previous implementations cann't handle. 
* **Fast**: The sampler can sample millions of tokens per second per multi-core node.
* **Lightweight**: Such big tasks can be trained with as few as tens of machines.

## Quick Start

Run ``` $ sh build.sh ``` to build lightlda.
Run ``` $ sh example/nytimes.sh ``` for a simple example.


## Reference

Please cite LightLDA if it helps in your research:

```
@inproceedings{yuan2015lightlda,
  title={LightLDA: Big Topic Models on Modest Computer Clusters},
  author={Yuan, Jinhui and Gao, Fei and Ho, Qirong and Dai, Wei and Wei, Jinliang and Zheng, Xun and Xing, Eric Po and Liu, Tie-Yan and Ma, Wei-Ying},
  booktitle={Proceedings of the 24th International Conference on World Wide Web},
  pages={1351--1361},
  year={2015},
  organization={International World Wide Web Conferences Steering Committee}
}
```

Microsoft Open Source Code of Conduct
------------

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.


## Question
### multiverso
If the downloading is too slowly when running the build shell, you can change the source for downloading. 
```
git clone -b multiverso-initial https://github.com/Microsoft/multiverso.git.
```
### zeromq
If the downloading is too slowly when running the build shell, you can change the source for downloading.
```https://github.com/zeromq/zeromq4-1/releases/download/v4.1.3/zeromq-4.1.3.tar.gz
```
### text2libsvm.py
If you want ro run the example/nytimes.sh in python3.x, you should rewrite text2libxvm.py that is running in python2.My revisement is below.
```
  File "/home/jockjo/LightLDA/example/text2libsvm.py", line 13
    print "Usage: python text2libsvm.py <docword.input> <vocab.input> <libsvm.output> <dict.output>"
                                                                                                   ^
SyntaxError: Missing parentheses in call to 'print'. Did you mean print("Usage: python text2libsvm.py <docword.input> <vocab.input> <libsvm.output> <dict.output>")?
```
line 13: print("Usage: python text2libsvm.py <docword.input> <vocab.input> <libsvm.output> <dict.output>")
```
Traceback (most recent call last):
  File "/home/jockjo/LightLDA/example/text2libsvm.py", line 39, in <module>
    if not word_dict.has_key(word_id):
AttributeError: 'dict' object has no attribute 'has_key'
```
line 39: if word_id not in word_dict.keys():
## tips
1. the root for example/nytimes/py is /example not /LightLDA, so you need to run the nytimes.py in LightLAD/example.
