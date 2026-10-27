# 시계열 분석·예측 학습 노트북

시계열의 추세·계절성·주기를 살펴보고 회귀 및 머신러닝 예측을 실습하는 노트북 모음이다. 기초 시계열 예제와 함께 주가 데이터 시각화, LSTM 예측, 뉴스 워드클라우드 실습을 포함한다.

## 학습 순서

| 노트북 | 내용 |
|---|---|
| `01_time_series_basic.ipynb` | 시계열 자료와 기본 처리 |
| `02_time_series_prediction_toy_model.ipynb` | 단순 예측 모델 |
| `03_trend.ipynb` | 추세 |
| `04_seasonality.ipynb` | 계절성 |
| `05_cycle.ipynb` | 주기 |
| `06_hybrid_models.ipynb` | 모델 결합 |
| `07_forecasting_with_machine_learning.ipynb` | 머신러닝 기반 예측 |

`stock_market_*.ipynb` 파일은 주가 시각화·회귀·LSTM 및 기사 분석 실습이다. `util.py`는 공통 보조 함수, `dataset/`은 도서 판매량·CO₂·전력 수요·독감 추이 등의 예제 CSV를 담는다.

## 기본 실행 환경

```powershell
python -m venv .venv
.\.venv\Scripts\python.exe -m pip install notebook pandas numpy matplotlib seaborn scikit-learn statsmodels
.\.venv\Scripts\python.exe -m notebook
```

기초 노트북부터 순서대로 열어 실행한다. 주가·기사 노트북은 pandas-datareader, yfinance, TensorFlow/Keras, requests, beautifulsoup4, KoNLPy, wordcloud 등 추가 패키지를 사용한다. 필요한 실습에 맞춰 설치하며 KoNLPy는 Java 환경도 확인한다. 외부 금융·기사 데이터 조회는 인터넷 연결과 현재 제공 API에 영향을 받는다.

## 작업 경로 설정

일부 노트북은 `import time_series_basic.util`과 `./time_series_basic/dataset/...`처럼 저장소의 **상위 폴더**를 기준으로 작성되어 있다. 노트북을 저장소 안에서 열었다면 첫 셀에서 다음과 같이 작업 경로를 맞출 수 있다.

```python
from pathlib import Path
import os
import sys

if Path.cwd().name == "time_series_basic":
    os.chdir(Path.cwd().parent)
sys.path.insert(0, str(Path.cwd()))
```

폴더 이름을 변경했다면 import와 데이터 경로도 함께 조정한다. 노트북별 파일 경로·폰트 설정을 확인한 후 셀을 순서대로 실행한다.

## 확인할 결과

원시 시계열, 추세와 계절성, 예측선과 실제 값의 차이, 모델별 오차를 확인한다. 주가 예측 실습은 학습 예제이며 실제 투자 성과나 미래 가격 예측력을 검증한 서비스가 아니다. 외부 데이터 조회 코드는 API 변경에 따라 수정이 필요할 수 있다.

## 참고 자료

기존 저장소에서 참조한 [zzhining/time_series_basic](https://github.com/zzhining/time_series_basic)의 학습 자료를 함께 참고한다. 자료를 활용한 학습·실습 저장소로 소개하며 모든 기초 예제를 독자적으로 제안한 알고리즘으로 설명하지 않는다. 추가 참고 자료는 『파이썬 라이브러리를 활용한 데이터 분석』과 TensorFlow 시계열 예측 튜토리얼이다.

---

[GitHub 저장소](https://github.com/pranpreten/time_series_basic) · [문서 작성 기준 코드](https://github.com/pranpreten/time_series_basic/tree/e67c374bc0d2bf7ecf6e65762f42c5bcb50152ea)
