# 1. Overview of NLP Tasks

总体而言，**自然语言处理**（Natural Language Processing）应涉及所有以人类的**语音**和**文字**为处理对象的研究，但是此处我们仅考虑针对**文本处理**的研究内容。

根据语言模型输入和输出类型的不同，现有的NLP 任务大致可以分为以下类别：

![Genral tasks of NLP](./images/general%20tasks.jpg)
(Source from: [Deep learning course by Hung-yi Lee](http://speech.ee.ntu.edu.tw/~tlkagk/courses/DLHLP20/TaskShort%20(v9).pdf))

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















