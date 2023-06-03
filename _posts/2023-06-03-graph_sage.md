---
title:  Inductive Representation Learning on Large Graphs (NIPS 2017)

excerpt: GNN, Graphsage , NIPS

toc : true
toc_sticky : true  

use_math: true

categories:
  - papers
tags:
  - papers
  - gnn
  - graphsage
---

# 1. Abstract

large 그래프에서 노드들에 대한 저차원 임베딩은 다양한 예측 테스트에 몹시 효과적이라는 것이 증명되어 왔다. 하지만 지금까지의 방법들은 그래프에서의 모든 노드가 임베딩 과정에서 고려되어야 한다. 이러한 방법들은 근본적으로 [transductive](https://en.wikipedia.org/wiki/Transduction_(machine_learning)) 하며 보지 못했던 새로운 노드에 대해서까지는 일반화하지 못한다. 이제
본 논문에서는 귀납적 방법의 프레임워크인 GraphSAGE 를 제안하는데,  