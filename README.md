# 1. Overview of NLP Tasks

总体而言，**自然语言处理**（Natural Language Processing）应涉及所有以人类的**语音**和**文字**为处理对象的研究，但是此处我们仅考虑针对**文本处理**的研究内容。

根据语言模型输入和输出类型的不同，现有的NLP 任务大致可以分为以下类别：
![123](./images/14684196_p0.jpg)
![Genral tasks of NLP](https://github.com/Daizt/Something-about-NLP/blob/master/images/general%20tasks.jpg)
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

## Search Engine
- `Input`: Sequences.
- `output`: Class.












