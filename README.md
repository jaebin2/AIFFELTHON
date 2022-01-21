 임베딩 시스템에서 온도컨트롤은 최적의 성능 유지를 위해 매우 중요한 요소이다. 온도가 너무 높으면 CPU or MPU의 클럭속도저하를 일으켜 퍼포먼스를 저하시키고 배터리의 공급효율을 떨어뜨려 시스템 작동에 문제를 발생시키는데 최적의 온도(36.5도)를 유지할 수 있는 시스템이 필요하다. 이러한 것은 전기에너지를 소모하여 시스템 운영에 차질이 없는 온도 구간까지 온도를 조절하는 기계적 액츄테이터들(Fan, Valve, Evaporator, hitter 등)을 이용하여 온도를 변화시킬 수 있다. 
 하지만 다양한 환경과 온도조절을 위한 기계적 장치들이 늘어남에 따라 얼마나 비용대비 효과적으로 시스템 열을 관리할 수 있는가의 문제를 발견할 수 있다. 우리는 엔지니어들이 일일이 기계적 장치를 조절하는데 인적비용, 전기에너지 소비비용을 절감하고 여러 환경에서 최고의 퍼포먼스를 보조할 수 있는 인공지능 모델을 만들것이다. 


데이터 전처리

결측치 처리, normalization
데이터 중에서 target 지정


모델 설계

예측 모델 LSTM: 데이터로 학습된 모델을 통해 target 값 예측
계산 모델 RL: PID 계산


결과 분석

적정 온도 도달, COP



phase 1
적정온도 계산을 어떻게 할 것인가? 어떤 모델이 적합한가? 수식을 통해 간단하게 계산이 가능하다면 예측모델 필요없이 계산된 온도로 제어하면 된다.


phase 2
어떤 모델을 사용하여 예측 할 것인가

LSTM


MLP
큰 차이는 없지만 MLP가 데이터가 적을 경우 성능이 더 좋다.
Prediction of Building’s Thermal Performance UsingLSTM and MLP Neural Networks
https://www.researchgate.net/publication/344884519_Prediction_of_Building's_Thermal_Performance_Using_LSTM_and_MLP_Neural_Networks


TD-LSTM 
데이터 기간이 긴 경우 효과적 프로젝트에 적합하지 않을 것 같다
TD-LSTM: Temporal Dependence-Based LSTM Networks for Marine Temperature Prediction
https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6263690/


phase 3
예측 모델을 학습시켜 최적의 조합을 찾는다. autoencoder? 모델 병렬화를 통해 여러 경우 도출 후 전력 계산


phase 4
