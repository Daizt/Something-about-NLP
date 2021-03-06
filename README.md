# 0. Top conferences in NLP
- [*dblp: computer science bibliography](https://dblp.uni-trier.de/db/conf/)

- [ACL: Association for Computational Linguistics](https://www.aclweb.org/portal/acl)
- [EMNLP: Empirical Methods in Natural Language Processing](https://www.aclweb.org/portal/emnlp)
- [NAACL: North American Chapter of the Association for Computational Linguistics](http://naacl.org/)
- [EACL: European Chapter of the Association for Computational Linguistics](http://www.eacl.org/)
- [COLING: International Conference on Computational Linguistics](https://coling2020.org/)
- [CoNLL: Conference on Natural Language Learning](https://www.conll.org/)

- [ICML: International Conference on Machine Learning](https://icml.cc/)
- [NeurIPS: Neural Information Processing Systems](https://nips.cc/)
- [AAAI: Association for the Advancement of Artificial Intelligence](https://www.aaai.org/)
- [SIGIR: Special Interest Group on Information Retrieval](http://sigir.org/)
- [LREC: Language Resources and Evaluation](http://lrec-conf.org/)

# 1. Overview of NLP Tasks

总体而言，**自然语言处理**（Natural Language Processing）应涉及所有以人类的**语音**和**文字**为处理对象的研究，但是此处我们仅考虑针对**文本处理**的研究内容。

根据语言模型输入和输出类型的不同，现有的NLP 任务大致可以分为以下类别：
<p align="center">
  <img width="800" height="600" src="./images/general-tasks.jpg">
</p>

## 1.1 Part-of-Speech Tagging (POS)
- `Input`: Sequence.
- `output`: Class for each token.

为文本中的每一个Token标注**词性**（动词、形容词、名词等），尤其是对于**一词多义**的情况较为重要，见下例：
```
John saw the saw.
(PN) (V) (D) (N)
```

## 1.2 Word Segmentation 
- `Input`: Sequence.
- `output`: Class for each token.

确定（中文）文本的词汇划分。

## 1.3 Parsing*

为给定文本做语法解析（生成语法树）。

## 1.4 Coreference Resolution*

指代消解，即找出文本中代词所指的对象。

## 1.5 Summarization
- Extractive summarization

  `Input`: Sequence.
  
  `output`: Class for each Token. (Here Token is a sentence.)
  
  从原文章中提取部分句子作为摘要。
  
- Abstractive summarization

  `Input`: Sequence.
  
  `output`: Sequence.
  
  将较长的输入文本更换表达方式后输出为较短的摘要。
  
## 1.6 Machine Translation
- `Input`: Sequence.
- `output`: Sequence.

## 1.7 Grammer Error Correction
- `Input`: Sequence.
- `output`: Sequence.

## 1.8 Sentiment Classification
- `Input`: Sequence.
- `output`: Class. (Positive, Negative)

## 1.9 Stance Detection 
- `Input`: Sequence(s).
- `output`: Class. (SDQC: Support, Denying, Querying, and Commenting.)

## 1.10 Natural Language Inference (NLI)
- `Input`: Sequences.
- `output`: Class. (contradiction, entailment, neutral)

能否从一个premise推断出一个hypothesis？
```
e.g.,
premise: A person on a horse jumps over a broken airplane.

hypothesis: A person is at a diner. (contradiction)
hypothesis: A person is outdoors. (entailment)
hypothesis: A person is training his horse for a competition. (neutral)
```

## 1.11 Search Engine
- `Input`: Sequences.
- `output`: Class.

## 1.12 Question Answering (QA)
- `Input`: Sequences.
- `output`: Sequence.

## 1.13 Natural Language Generation (NLG)
- `Input`: Sequence.
- `output`: Sequence.

## 1.14 Natural Language Understanding (NLU)
- Intent Classification (意图分类)
  - `Input`: Sequence.
  - `output`: Class.

- Slot Filling
  - `Input`: Sequence.
  - `output`: Class for each token.
  
  从给定文本中筛选符合要求的内容，例如：
  ```
  Slot: 入住日，退房日
  Input ：我 打算 在 6月7号 入住，6月9号 退房。
  Output：(N) (N) (N) (Y)   (N)    (Y)   (N)
  ```

## 1.15 Knowledge Graph*
知识图谱的基本组成：entity，relation。要建立知识图谱，需要使用模型从资料库中识别出各种不同的entity，然后根据资料建立各个entity之间的relation。
- Name Entity Recognition (NER)
  - `Input`: Sequence.
  - `output`: Class for each token.
 
- Relation Extraction
  - `Input`: Sequences.
  - `output`: Class or Sequence.
  
## 1.16 Benchmarks*
- GLUE & Super GLUE

  The **General Language Understanding Evaluation benchmark (GLUE)** is a tool for evaluating and analyzing the performance of models across a diverse range of existing natural language understanding tasks. Models are evaluated based on their average accuracy across all tasks.
  - [GLUE Website](https://gluebenchmark.com/)
  - [Super GLUE Website](https://super.gluebenchmark.com/)
  - [Chinese Version](https://www.cluebenchmarks.com/)
  
  
- DecaNLP

  The **Natural Language Decathlon (decaNLP)** is a new benchmark for studying general NLP models that can perform a variety of complex, natural language tasks. By requiring a single system to perform **ten disparate natural language tasks**, decaNLP offers a unique setting for multitask, transfer, and continual learning.
  - [DecaNLP Website](http://decanlp.com/)
  

# 2. BERT and its family
## 2.1 The pre-trained model
Use the model to represent each token by a **embedding vector**. 
At first, we have **uncontextualized** word embedding:

- Word2vec ([Mikolov, et al., NIPS'13](https://papers.nips.cc/paper/5021-distributed-representations-of-words-and-phrases-and-their-compositionality.pdf))
- Glove ([Pennington, et al., EMNLP’14](https://www.aclweb.org/anthology/D14-1162.pdf))
- FastText ([Bojanowski, et al., TACL’17](https://www.mitpressjournals.org/doi/pdfplus/10.1162/tacl_a_00051?source=post_page---------------------------&))
 
**Drawbacks**: The same token must have the same embedding. 即无法解决**一词多义**问题，因为没有考虑语境。
 
So here comes the **contextualized** word embedding: 
 
- Transformer ([Vaswani, et al., NIPS'17](https://papers.nips.cc/paper/7181-attention-is-all-you-need.pdf))
- BERT ([Devlin, et al., arXiv'18](https://arxiv.org/pdf/1810.04805.pdf?source=post_elevate_sequence_page---------------------------))
- ELMO ([Peters, et al., NAACL'18](https://arxiv.org/pdf/1802.05365.pdf%E3%80%91))
- ERNIE ([Sun, et al., ACL'19](https://arxiv.org/pdf/1904.09223))
- XLNet ([Yang, et al., NeurIPS'19](https://papers.nips.cc/paper/8812-xlnet-generalized-autoregressive-pretraining-for-language-understanding.pdf))
- MASS ([Song, et al., ICML'19](https://arxiv.org/pdf/1905.02450))
- BART ([Lewis, et al., arXiv'19](https://arxiv.org/pdf/1910.13461))
- UniLM ([Dong, et al., NeurIPS'19](https://papers.nips.cc/paper/9464-unified-language-model-pre-training-for-natural-language-understanding-and-generation.pdf))
- RoBERTa ([Liu, et al., arXiv'19](https://arxiv.org/pdf/1907.11692))
- structBERT ([Want, et al., ICLR'20](https://arxiv.org/pdf/1908.04577))
- GPT ([Alec, et al., 2018](https://www.cs.ubc.ca/~amuham01/LING530/papers/radford2018improving.pdf))
- GPT-2 ([Alec, et al., 2019](https://www.ceid.upatras.gr/webpages/faculty/zaro/teaching/alg-ds/PRESENTATIONS/PAPERS/2019-Radford-et-al_Language-Models-Are-Unsupervised-Multitask-%20Learners.pdf))
 
But the models are too big!! Thus researchers have tried many ways to **compress** them:
 
- [All The Ways You Can Compress BERT](http://mitchgordon.me/machine/learning/2019/11/18/all-the-ways-to-compress-BERT.html)
- Distill BERT ([Sanh, et al., NeurIPS workshop'19](https://arxiv.org/pdf/1910.01108))
- Tiny BERT ([Jian, et al., arXiv'19](https://arxiv.org/pdf/1909.10351))
- Mobile BERT ([Sun, et al., ACL'20](https://arxiv.org/pdf/2004.02984))
- ALBERT ([Lan, et al., ICLR'20](https://arxiv.org/pdf/1909.11942))
- Transformer-XL ([Dai, et al., ACL'19](https://arxiv.org/pdf/1901.02860.pdf]))
- Reformer ([Kitaev, et al., ICLR'20](https://arxiv.org/pdf/2001.04451))
- Longformer ([Beltagy, et al., arXiv'20](https://arxiv.org/pdf/2004.05150))
 
## 2.2 How to pre-train
- Pre-training by Translation

  通过使模型（encoder）参与翻译任务来达到预训练的目的，缺点是需要大量的sentence pairs。

- Pre-training by Predicting next token

  这种预训练方式不需要大量的标注数据，只需要机器根据输入句子中的**其它token**预测下一个token即可。
  
  - 可以只根据待预测token**之前**的内容进行预训练
  - 可以同时参考待预测token**前后**的内容进行预训练，如BERT，ELMO的做法
   
## 2.3 Transfer & Fine-tune
当获得了预训练模型后，我们可以在此基础上添加一些Task-specific Layer来获得适用于场景的模型。具体而言，NLP任务的输入、输出类型大体有以下类别：
```
Input: One sentence, Multiple sentences.
```
```
Output: One class, Class for each token, General sequence.
```
- `Input`: One sentence or Multiple sentences

  One sentence的情况不必多说，直接输入pre-trained model即可；对于Multiple sentences的情况，可以采用特殊符号连接多组句子然后输入到模型当中：
  
<p align="center">
  <img width="400" height="180" src="./images/multi-sentence-input.jpg">
</p>

- `Output`: One class

  当输出为one class时，可以在input sequence首位加入一个特殊token用以“告诉”model输出一个考虑整个input sequence的embedded vector，然后将其作为task specific layer的输入最终输出一个class；还可以直接将所有的embedded vector直接作为task specific layer的输入，然后得到一个class结果。

<p align="center">
  <img width="300" height="300" src="./images/output-one-class.jpg">
</p>

- `Output`: Class for each token

  当需要为每一个token输出一个class时做法也非常直觉，将所有的embedded vector直接输入到下一层task specific layer（可以为RNN等）即可。
  
<p align="center">
  <img width="260" height="310" src="./images/output-class-for-each-token.jpg">
</p>

- `Output`: General Sequence

  当输出为sequence时，可以直接将pre-trained model看作是encoder，然后再连接一个decoder以实现seq2seq模型。
  
<p align="center">
  <img width="500" height="240" src="./images/output-general-sequence-1.jpg">
</p>

- `Output`: General Sequence

  还有一种做法是直接将pre-trained model当作decoder来用。此时我们在input sequence后添加一个特殊token，然  后将该特殊token对应的embedded vector输入到task specific layer中得到第一个输出token，接下来按照decoder的用法将输出的token再次输入到pre-trained model中以获得后续的output token，直到出现`<EOS>`为止。
  
<p align="center">
  <img width="500" height="330" src="./images/output-general-sequence-2.jpg">
</p>

在根据输入、输出格式设计好整体模型架构后，便可以在新的数据集上进行fine-tune。具体而言，可以固定pre-trained model参数不变而只更新task specific layer，也可以二者一起更新。对于pre-trained model同步更新的训练方式，由于任务种类繁多且预训练模型本身巨大，所以该训练方式必然需要存储多组预训练模型的参数。为解决这一问题，研究者又提出了Adapter的思路。
 - [Stickland, et al., ICML'19](https://arxiv.org/pdf/1902.02671) 
 - [Houlsby, et al., ICML’19](https://arxiv.org/pdf/1902.00751.pdf?source=post_page---------------------------)

  
  
  















