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
이것은 타겟 노드들과 그들의 특정한 상호작용을 지정하는 중간 컨텍스트 노드들의 multi-partite 네트워크를 모델링하는
것으로 이루어진다. 이웃 집계 과정에 대하여서는, 중간 컨텍스트에 기반한 이웃으로 하는 타겟 노드들을  처리하여 
interaction contextualization 을 달성하기 위해 
논문에서는 피쳐 단계에서의 문맥을 고려한 마스킹 연산과 노드 단계에서의 어텐션 메커니즘을 고안하였다.  

**그냥 번역하니까 복잡한데, hogeneous 그래프, 단일 임베딩보다 더 복잡한 것을 다루는 방법론을 사용한다는 뜻으로 이해됨.**

**여기서 어텐션 메커니즘과 contextual masking 을 사용함.**

결론적으로, 그래프 콘볼루션 연산에서 서로 다른 상호작용들과 다양한  facets 를 포착하는 노드들에 대한 다중 임베딩을 계산한다.
이는 미세 조정된 다운스트림 테스크 적용에 유용하게 사용될 수 있다.

(나머지는 실험 세팅 얘기라서 생략함)

# 1. Introduction

![](https://user-images.githubusercontent.com/113276452/243555339-84c875c0-87ab-4165-a7bd-edf7acef330e.png)

그래프 콘볼루션 신경망 모형들은 거대한 그래프 데이터로부터 정보룰 추출하는 테스크에 있어서 상당한 주목을 받고 있다. 

이는 spcetral 한
그래프 이론과 fundmental 한 연결성을 가지고 있으며, 따라서 증명 가능한 representation 능력을 가지고 있기 때문이고, 
또한 몇몇 그래프 마이닝 밴치마크들에서 보여주는 그들의 유망한 성능 때문이다. 

GCN 모형들의 이러한 능력을 이용하기 위해서,
GraphSAGE 는 고정된 크기의 이웃 샘플링을 통한 batch-wise 훈련을 활용한다. 이는 나중에 Pinterest 에서 개발한 PinSAGE 라는 강건한
enterprise-scale 버전으로 적용되기도 해였다. Pinsage 는 industry-scale의 pin-board 그래프를 기반으로 유사한 pin 들을
추천하는 데 있어서 몹시 효과적이었다. 

그러나, 지금까지의 GCN 들의 주요한 한계점 중 하나는 여러 측면의 노드의 성질들과 복잡한
노드간 상호작용들을 구별해내지 못한다는 것이다. 이는 모형이 node links 를 모두 homogeneous 하게 취급하기 떄문이다. 


Figure 1(a)  에서 볼 수 있듯, 실제 현실의 산업 플랫폼에서 SOTA 모형인 GCNs 들은 모든 연관된 노드들을 하나의 임베딩 공간에 섞어버린다.

**Present work**. 이 논문에서, 하나의 네트워크에 있는 노드들이 서로 다른 이유들로 연결되어 있으며, 그러므로 서로 다른 방법으로
연결되어 있고, 하나의 임베딩으로 이를 포착할 수 없다는 것을 주장한다. 결론적으로, MULTISAGE 를 제안하는데, 이는 컨텍스트화된
다중 임베딩에 대한 참신한 아이디어에 근본을 두고 있다고 할 수 있다. ; 노드들의 컨텍스트화된 상호작용을 포착하는 네트워크 
노드들에 대한 다중 임베딩을 그에 대응하는 다중 임베딩 공간에서 계산하는 것. Figure 1(b) 에 MultiSAGE 가 다중 임베딩 공간에서
다양한 컨텍스트 하에서 쿼리와 관련된 노드들을 검색하고 조직화하는 걸 보여준다.

MultiSAGE 는 두 가지 연구 질문에 대한 대답이다.

**RQ 1. 어떻게 적절한 컨텍스트를 찾는가(How to find proper context?)**

현실 네트워크의 네트워크는 자주 multipartite 하다. 즉, 네트워크가 다양한 타입의 노드들을 가지고 있고 이는 
자연스럽게 노드간 상호작용에 대한 컨텍스트를 제공한다. 이러한 점 때문에, 타겟 노드가 컨텍스트 노드를 multipartite
네트워크로 모델링하는 것이 유용하다.

Pinterest의 예시를 보면 개인 board 에 'pin' 을 하여 유저들끼리 상호작용을 한다. 이렇게 만들어진 pin-board 그래프는
multipartite (여기선 bipartite) 하다. pin node 를 target, board node 를 context node 로 취급한다.
이것에 대한 직관은 매우 자연스럽다. 예를 들어, 두 개의 pin 이 fashion board 와 path 로 연결되어 있다면
두 pin 의 임베딩은 가까울 것이다.

**RQ 2. 어떻게 컨텍스트를 이용하는가(How to leverage context?)**
MultiSAGE 는 GCN 에 상호작용 컨텍스트화를 핵심적인 이웃 간 콘볼루션 연산에 주입하여 확장한 것이다.
각 타겟 노드에 대해 서로 다른 컨텍스트 노드들이 암시하는 조건 하에서 동적으로 다중 임베딩을 계산한다.

특히, 유연한 피쳐 수준 임베딩의 projection 을 위한 학습가능한 컨텍스트의 마스킹 연산과
그래프 콘볼루션 과정 중에서 노드 수준의 이웃 reweighing 를 위한 세 가지의
컨텍스트 attention 매커니즘을 설계한다.

# 2. Our Approach

## 2.1 Preliminaries

![](https://user-images.githubusercontent.com/113276452/243671048-a9199ea0-b3bf-48c5-a430-8392f8577307.png)

GCN 에서 ($$l+1$$) 번쨰 레이어의 아웃풋은 식 (1) 처럼 계산된다. 이때,

-  $$\tilde{A}$$ : self-connection 을 포함한 인접행렬(Adjacency Matrix)
-  $$\tilde{D}$$ : 대각성분이 $$\sum_{j} \tilde{A}_{ij}$$ 인 대각행렬
-  $$W^{l}$$ : 학습 가능한 레이어 l의 가중치 행렬 
-  $$\sigma(\cdot)$$ : 비선형 함수 
-  $$H^{l} \in R^{N \times D_l}$$ : l 번쨰 레이어의 아웃풋, $$H^{0}$$ 은 처음에 입력한 노드 피쳐

![](https://user-images.githubusercontent.com/113276452/243671123-88b31158-ea08-43b9-9db5-4f3059cbaee4.png)



![](https://user-images.githubusercontent.com/113276452/243671227-b596b59e-11fa-4091-8025-0e124c3f2d7c.png)



## 2.2 MultiSAGE

## 2.3 Web-scale Implementation of MultiSAGE

# 3. Experiments