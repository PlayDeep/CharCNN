# CharCNN

![MIT](https://img.shields.io/badge/license-MIT-blue.svg)

This repository contains my implementation using [Textify](https://github.com/mhjabreel/Textify) for Character-level Convolutional Networks for Text Classification. It can be used to reproduce the results in the following article:

Xiang Zhang, Junbo Zhao, Yann LeCun. [Character-level Convolutional Networks for Text Classification](http://arxiv.org/abs/1509.01626). Advances in Neural Information Processing Systems 28 (NIPS 2015)

![Alt text](ccnn.png?raw=true "The model")

## How to use
First, install Textify:.
```sh
    pip install git+https://github.com/mhjabreel/Textify.git
```

Then, run the follwoing command to train the model:
```sh
    textify train_and_eval --config configs/model.yml configs/data.yml configs/train.yml
```

## License

Copyright (c) 2016 Mohammed Jabreel

The source code is distributed under the MIT license.


## AG及新闻主题分类数据集
AG是由ComeToMyHead超过一年的努力，从2000多不同的新闻来源搜集的超过1百万的新闻文章
ComeToMyHead是一个学术新闻搜索引擎，开始于2004年7月
 http://www.di.unipi.it/~gulli/AG_corpus_of_news_articles.html
该数据集由学术社区提供，用于研究分类，聚类，信息获取(rank，搜索)...等非商业活动

两个格式版本: db 和 xml

DB Table

+-------------+--------------+------+-----+-------------------+-------+
| Field       | Type         | Null | Key | Default           | Extra |
+-------------+--------------+------+-----+-------------------+-------+
| source      | varchar(32)  |      | PRI |                   |       |
| url         | varchar(255) |      | PRI |                   |       |
| title       | text         | YES  | MUL | NULL              |       |
| image       | varchar(255) | YES  |     | NULL              |       |
| category    | varchar(32)  |      | PRI |                   |       |
| description | text         | YES  |     | NULL              |       |
| rank        | int(11)      | YES  |     | NULL              |       |
| pubdate     | timestamp    | YES  |     | CURRENT_TIMESTAMP |       |
| video       | varchar(255) | YES  |     | NULL              |       |
+-------------+--------------+------+-----+-------------------+-------+

其中的主题分类数据集由 Xiang Zhang (xiang.zhang@nyu.edu) 从以上数据集中构建
https://github.com/mhjabreel/CharCNN/tree/master/data/ag_news_csv
它来自于原始语料库中4个最大的类
每个类包含30，000训练样本和1900测试样本，因此总的训练样本是12，000，总的测试样本是7600

文件classes.txt包含包含类名称,即：
World
Sports
Business
Sci/Tec

文件train.csv 和 test.csv 包含了逗号分隔的3栏，分别是 类索引(1-4),标题和描述
标题和描述都有双引号""包含，其中的内部引号由双重引号标出，
新行由\n分隔

