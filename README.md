# K_Data_Project_2023

## overview

전세사기는 주로 사회 초년생과 서민층에서 발생하는 문제로, 전세계약 관련 지식이 부족할수록 피해 위험이 증가합니다. 이에 따라 우리는 전세사기 유형을 분석하고 예방 방안을 제시하고자 이 프로젝트를 진행하게 되었습니다. 기존 선행 연구들은 주로 지역구 단위의 위험 지역을 선정하고, 한 가지 유형의 사기만을 대상으로 위험도를 도출했습니다. 그러나 이러한 접근은 전세사기의 다양한 유형을 충분히 반영하지 못했습니다. 이를 해결하기 위해 본 프로젝트에서는 개별 부동산 매물을 대상으로 세분화된 분석을 진행하고 여러 유형의 전세사기 위험도를 동시에 도출할 수 있는 방법을 제시하고자 했습니다.

### <기여한 부분만 작성>

**[데이터 수집]**

**전세사기 매물 데이터**

전세사기 피해 매물 및 비피해 매물 데이터를 수집하기 위해 등기부등본과 경매 매각명세서를 활용하여 피해 발생 시점과 전세계약 데이터를 확보했습니다. 또한 다양한 변수들을 기준으로 사기 유형을 구분할 수 있는 데이터를 라벨링하고, 부족한 데이터는 대체 가능한 형태로 보완했다.

![전세사기 피해 매물 데이터 수집방법 1](https://i.esdrop.com/d/f/roqIf5Zmhy/06npCTlWX2.png)
![전세사기 피해 매물 데이터 수집방법 2](https://i.esdrop.com/d/f/roqIf5Zmhy/c0RDFCfuQN.png)
![전세사기 피해 매물 데이터 수집방법 3](https://i.esdrop.com/d/f/roqIf5Zmhy/Yhvlg5VHzY.png)

경매 사이트에 올라와있는 매물 중 여러 채의 부동산을 가지고 있는 집주인의 이름을 감정평가서를 통해 확인하였고, 이를 전세사기범 실명과 대조함으로써 해당 매물이 전세사기 피해 매물임을 특정하였다.

![전세사기 피해 매물 데이터 수집방법 4](https://i.esdrop.com/d/f/roqIf5Zmhy/vcEUUiQOvF.png)
![전세사기 피해 매물 데이터 수집방법 5](https://i.esdrop.com/d/f/roqIf5Zmhy/IxgzM8189a.png)

-> 경매 매각명세서를 통해 피해자의 전세계약 시점을 확인하였고, 첫 전세계약 시점부터 경매 개시 결정일까지의 등기부기록을 입력하였다.

**전세사기 아닌 매물 데이터**

첫 전세계약일부터 두 번째 전세계약일 사이의 등기부기록을 기입하였다.

![전세사기 아닌 매물 데이터 수집방법 1](https://i.esdrop.com/d/f/roqIf5Zmhy/Pf1q5O5jaq.png)
![전세사기 아닌 매물 데이터 수집방법 2](https://i.esdrop.com/d/f/roqIf5Zmhy/8EoEsIuyIx.png)
![전세사기 아닌 매물 데이터 수집방법 3](https://i.esdrop.com/d/f/roqIf5Zmhy/i3Im6vpakR.png)
![전세사기 아닌 매물 데이터 수집방법 4](https://i.esdrop.com/d/f/roqIf5Zmhy/xXVVDY6XXh.png)
![전세사기 아닌 매물 데이터 수집방법 5](https://i.esdrop.com/d/f/roqIf5Zmhy/DB40GcEvPJ.png)

**[데이터 전처리]**

전처리 과정에서 y축의 '근저당' 항목과 관련하여 집중적으로 이상치가 발견되었다.

**전세사기 데이터**
![전세사기 데이터_1](https://i.esdrop.com/d/f/roqIf5Zmhy/LssWxUYkaV.png)
![전세사기 데이터_2](https://i.esdrop.com/d/f/roqIf5Zmhy/eRB1tDSzIl.png)

-> 데이터 양 부족으로 의미있는 데이터로 남겨두기로 결정하였다.

-> 근저당의 평균치가 높아 이상치 제거를 하지 않았다.

**전세사기 아닌 데이터**
![전세사기 아닌 매물 데이터_1](https://i.esdrop.com/d/f/roqIf5Zmhy/fHYt7xNbjC.png)
![전세사기 아닌 매물 데이터_2](https://i.esdrop.com/d/f/roqIf5Zmhy/2pycEizYW9.png)

-> 평균치를 크게 상회하는 근저당이 발견되었고 데이터를 재수집하여 해당 매물이 아닌 건물 전체에 대한 근저당이 잡혀 있음을 확인하였고 이러한 이상치를 제거하였다.

- 등기부등본에 공동담보목록이 없는 상태
  
  - 개별 근저당을 구할 수 없는 데이터 ‘잘못된 데이터이기에 제거’

**[EDA]**

EDA를 통해 변수들의 특성을 대략적으로 살펴보았다.

**전세사기 데이터**
![전세사기 데이터_1](https://i.esdrop.com/d/f/roqIf5Zmhy/AO7GH82wO3.png)
![전세사기 데이터_2](https://i.esdrop.com/d/f/roqIf5Zmhy/RnFYjPsJyO.png)

**전세사기 아닌 데이터**
![전세사기 아닌 데이터_1](https://i.esdrop.com/d/f/roqIf5Zmhy/o9SMWJ9QuZ.png)
![전세사기 아닌 데이터_2](https://i.esdrop.com/d/f/roqIf5Zmhy/lLvvOwco8G.png)

-> 전세사기 : 전세가율 평균 ↑, 가압류 키워드 확률 ↑, 신탁 ↑, 근저당 ↑

**[데이터 가공]**

제한된 시간과 비용으로 데이터 수집에 한계가 있었다.

![데이터 가공_1](https://i.esdrop.com/d/f/roqIf5Zmhy/zkEdyZClEb.png)
![데이터 가공_2](https://i.esdrop.com/d/f/roqIf5Zmhy/a6hHudI0Hr.png)

-> 그 결과 imbalanced data & insufficient data 문제를 발견하였다.

![데이터 가공_3](https://i.esdrop.com/d/f/roqIf5Zmhy/X0LZ9Llciy.png)

![데이터 가공_4](https://i.esdrop.com/d/f/roqIf5Zmhy/7Z4JXELRt6.png)

위 문제를 해결하기 위해 오버샘플링을 진행하였다. 이에 **SMOTE** 알고리즘을 사용하였고, 오버샘플링 자체가 갖고 있는 과적합을 완전히 피할 순 없었다.
