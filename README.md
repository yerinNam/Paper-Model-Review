# Paper-Model-Review

**Microsoft-Phi2**
<br/>
"Phi"는 마이크로소프트 회사에서 출시한 SLM(소형 언어 모델) 이다.
Phi-2의 주요 인사이트는 두 가지이다.
<br/>
- Phi가 가벼우면서도 높은 성능을 낼 수 있는 핵심 요인은 "훈련 데이터의 질"이다.
마이크로소프트는 이를 극단으로 끌어올려 '교과서 수준의 품질을 갖춘 데이터'라고 하며 
이를 중점으로 훈련시켰다. <br/>
- Phi-1.5에서 Phi-2로 모델을 확장하는 과정은 Tranfer Learning의 한 종류로 볼 수 있다.
<br/>
<나의 생각>
<br/>
GPU의 중요성이 올라가거나 모델의 경량화가 매우 중요할 거라고 생각하였는데 실제로도 그러한 모델들이 개발되고 있는 거 같다.
이렇게 되면 GPU 같은 하드웨어 중요성은 일반적인 시장의 예상보다 훨씬 적을 수 있다. 곧 현재 수준의 하드웨어로도 온디바이스 ai가 구현이 가능할 수 있다는 것이다.
또한, Phi 역시도 GPT의 문제점인 거짓 응답과 유해성에 관련해서 아직 약한 것을 알 수 있다.
이는 앞으로의 연구 방향이 이와 관련될 것이라고 예상된다.
그리고, Task는 Gpt보다 다 적은 컴퓨팅 파워로 Q&A와 코드 생성 등에 관한 부문에 많이 쓰일 거 같다.
이 외에도 LM이라는 부문에서 평가 지표는 여전히 발전되고 있으며 Classification 문제에서
Acc처럼 어느 하나의 평가 지표에서 평가를 그치는 게 아니라
다방면으로 평가를 해야함을 알 수 있다.
<br/>
<br/>

**Solar**
<br/>
 Solar는 Llama2에 DUS 방식을 추가한 모델이다. 최근 언어 모델의 크기가 커짐에 따라, 이들을 효율적으로 확장하는 것은 중요한 과제인데 DUS는 이러한 필요성에 대응하여 개발되었다. DUS는, 기존 모델의 층(layer)을 복제하여 모델의 깊이를 증가시키는 방식이라고 할 수 있다. 기존 ‘Mixture of Experts (MoE)’ 방식과 달리, Train 및 Inference 프레임워크에 복잡한 변경을 요구하지 않는다. <br/>
DUS를 진행한 후, SOLAR 10.7B 모델에 대해 instruction tuning과 alignment tuning을 진행한다.<br/>
- Instruction tuning <br/>
Instruction tuning 단계에서는 QA 포맷으로 모델이 instruction을 따르도록 하는 방식을 사용했다. 
대부분 오픈소스 데이터를 사용했지만, 수리 능력을 향상하기 위해 mathQA 데이터도 활용하였다. <br/>
- Alignment tuning <br/>
Instruction tuning된 모델에 대해 DPO(direct preference optimization) 학습을 수행하였다.
이때 DPO는 기존의 강화 학습에서 요구되는 보상 모델링 단계를 건너뛰고 선호도 데이터를 직접 사용하여 언어 모델을 최적화하는 접근 방식이다. 
DPO는 복잡한 보상 함수를 명시적으로 모델링하고 최적화하는 대신, 선호도 데이터를 통해 직접 정책(policy)을 최적화함으로써, 언어 모델의 출력을 사용자의 선호와 더 잘 일치시키는 것을 목표로 한다.<br/>

<br/><나의 생각><br/>
DUS가 모델을 복제해서 깊이만 늘린다면 그냥 애초에 깊이를 깊게 해서 학습시키거나 굳이 자르지 않고 뒤에 바로 붙일 수 있는데 왜 중간층을 자르지?라는 의문감이 들었었다.
하지만, 단순히 층을 늘리면 그만큼 GPU와 학습 시간도 늘어난다.
그리고 층을 잘라서 붙이지 않으면 이음새의 레이어 거리 문제가 발생한다. <br/>
즉, DUS는 LLM을 업스케일링하는 동시에 이음새의 레이어 거리 문제를 완화하고, 
사전 훈련된 가중치의 활용도를 높이고, MoE 모델과 관련된 복잡성을 방지하는 효과적인 방법을 제공한다는 것을 알 수 있었다.<br/>
이 기법은 나중에 모델을 개발할 때 GPU 소모를 줄이는 아주 좋은 방법이 될 거라고 생각한다.
