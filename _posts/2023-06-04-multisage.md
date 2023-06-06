---
title:  MultiSage - Empowering GCN with Contextualized Multi-Embeddings on Web-Scale Multipartite Networks (KDD 2020)

excerpt: GNN, Multi-sage , KDD

toc : true
toc_sticky : true  

use_math: true

categories:
  - papers
tags:
  - papers
  - gnn
  - attention
  - multisage
---

# 0. Abstract
그래프 콘볼루션 신경망(GCN 등) 모형들은 GNN 에서 강력한 성능을 보이고 있다. 준지도학습 기반의 end-to-end 방법으로 학습하여
GCN 모형들은 노드 피쳐와 그래프 구초를 통합하는 방법을 학습하여 다양한 추천 시스템과 같은 다운스트림 테스크에 적용할 수 있는 높은 퀄리티의 임베딩을
생성한다. 

그러나, 지금까지의 GCN 모형들은 homogeneous 한 그래프에서만 작업을 수행하여 왔고, 각 노드에 대해
하나의 임베딩만을 고려했다. 이는 현실 네트워크들의 multi-facet 한 특성과 노드간의 복잡한 상호작용을
충분히 모델링하지 못한다. 이 논문에서, 저자는 contextualized GCN engine 이라는 것을 실현한다.
이것은 타겟 노드들과 그들의 특정한 상호작용을 지정하는 중간 문맥상의 노드들의 multi-partite 네트워크를 모델링하는
것으로 이루어진다. 이웃 집계 과정에 대하여서는, 중간 문맥상에 기반한 이웃으로 하는 타겟 노드들을  처리하여 
interaction contextualization 을 달성하기 위해 
논문에서는 피쳐 단계에서의 문맥을 고려한 마스킹 연산과 노드 단계에서의 어텐션 메커니즘을 고안하였다.  

**그냥 번역하니까 복잡한데, hogeneous 그래프, 단일 임베딩보다 더 복잡한 것을 다루는 방법론을 사용한다는 뜻으로 이해됨.**

**여기서 어텐션 메커니즘과 contextual masking 을 사용함.**