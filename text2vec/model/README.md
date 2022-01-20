# CoSENT model

比Sentence-BERT更有效的句向量方案

## 
- 参考: https://github.com/bojone/CoSENT
- 对应博客：https://kexue.fm/archives/8847
- 孟子预训练模型: https://github.com/Langboat/Mengzi


## 实验结果
实验效果来了。 预训练模型用的是孟子, 学习率2e-5,batch_size=64,等价苏神代码中的batch_size=32. 只用了训练集训练，然后在测试集上做测试。 分别训练了5个epoch，使用斯皮尔曼系数评价

指定不同数据集，只需在config.py文件中，修改下面两个参数:  
parser.add_argument('--train_data', default='./data/STS-B/STS-B.train.data', type=str, help='训练数据集')  
parser.add_argument('--test_data', default='./data/STS-B/STS-B.test.data', type=str, help='测试数据集')

### 本项目实验结果
test测试集的评估结果：

| | ATEC | BQ | LCQMC | PAWSX | STS-B |
| :-: | :-: | :-: | :-: | :-: | :-: |
| MengZi+CoSENT | **50.5270** | **72.2789** | **78.6981** | **?** | **80.15** |
| MacBERT+CoSENT |  | **72.2789** | **78.6981** | **?** | **79.33** |

### 苏剑林的结果
train训练、test测试：

| | ATEC | BQ | LCQMC | PAWSX | STS-B | Avg |
| :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| BERT+CoSENT | **49.74** | **72.38** | 78.69 | **60.00** | **80.14** | **68.19** |
| Sentence-BERT | 46.36 | 70.36 | **78.72** | 46.86 | 66.41 | 61.74 |
| RoBERTa+CoSENT | **50.81** | **71.45** | **79.31** | **61.56** | **81.13** | **68.85** |
| Sentence-RoBERTa | 48.29 | 69.99 | 79.22 | 44.10 | 72.42 | 62.80 |

