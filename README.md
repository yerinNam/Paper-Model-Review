# Paper-Model-Review

**Microsoft-Phi2**
"Phi"는 마이크로소프트 회사에서 출시한 SLM(소형 언어 모델) 이다.
Phi-2의 주요 인사이트는 두 가지이다.
'''
1) Phi가 가벼우면서도 높은 성능을 낼 수 있는 핵심 요인은 "훈련 데이터의 질"이다.
마이크로소프트는 이를 극단으로 끌어올려 '교과서 수준의 품질을 갖춘 데이터'라고 하며 
이를 중점으로 훈련시켰다.
2)  Phi-1.5에서 Phi-2로 모델을 확장하는 과정은 Tranfer Learning의 한 종류로 볼 수 있다.
'''
<나의 생각>'''
GPU의 중요성이 올라가거나 모델의 경량화가 매우 중요할 거라고 생각하였는데 실제로도 그러한 모델들이 개발되고 있는 거 같다.
이렇게 되면 GPU 같은 하드웨어 중요성은 일반적인 시장의 예상보다 훨씬 적을 수 있다. 곧 현재 수준의 하드웨어로도 온디바이스 ai가 구현이 가능할 수 있다는 것이다.
또한, Phi 역시도 GPT의 문제점인 거짓 응답과 유해성에 관련해서 아직 약한 것을 알 수 있다.
이는 앞으로의 연구 방향이 이와 관련될 것이라고 예상된다.
그리고, Task는 Gpt보다 다 적은 컴퓨팅 파워로 Q&A와 코드 생성 등에 관한 부문에 많이 쓰일 거 같다.
이 외에도 LM이라는 부문에서 평가 지표는 여전히 발전되고 있으며 Classification 문제에서
Acc처럼 어느 하나의 평가 지표에서 평가를 그치는 게 아니라
다방면으로 평가를 해야함을 알 수 있다.

