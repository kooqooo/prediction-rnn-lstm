# RNN과 LSTM을 활용한 서울시 코로나19 신규 확진자 수 시계열 데이터 예측
Prediction of time series data on the number of newly confirmed COVID-19 cases in Seoul using RNN and LSTM

# 개요

[논문(사회적 변수를 고려한 LSTM 기반 코로나19 일별 확진자 수 예측 기법)](https://www.dbpia.co.kr/journal/articleDetail?nodeId=NODE11034402)의 실험을 재현하고자 한다. RNN과 LSTM을 사용하여 각각 1, 7, 14일 후의 서울시의 코로나19 추가 확진자 수 예측을 위한 코드이다.

- PyTorch를 사용하였다.
- 코드에서 GPU 가속을 사용하는데, 가끔 메모리 누수 문제가 있어서 다른 코드가 실행이 어려운 경우가 있거나 이전 연산이 영향을 주는 경우가 있다. 커널을 재시작을 눌러 이 문제를 해결 할 수 있다.

# 데이터

- 논문의 변수와 맞게 직접 데이터 파일을 구성하였다.
이 파일은 2020년 2월 5일 ~ 2022년 12월 29일의 데이터를 가지고 있다.
이 데이터 파일은 df.csv이다.
- [논문](https://www.dbpia.co.kr/journal/articleDetail?nodeId=NODE11034402)에 따르면, 2020년 1월 24일 ~ 2021년 8월 3일의 데이터를 사용한다.
논문과의 비교를 위해 2020년 2월 5일 ~ 2021년 8월 3일의 데이터 파일을 생성하였다.
이 데이터 파일은 df_short.csv이다.
- [논문 저자의 github](https://github.com/17011813/Attention-COVID)에서 직접 코드와 [데이터(tr.csv)](https://github.com/17011813/Attention-COVID/blob/main/tr.csv)를 확인할 수 있었는데 저자가 만든 데이터를 사용하여 직접 실험을 진행하였다.
이 데이터 파일은 tr.csv이다.

# 실험 과정

1. df의 RNN
2. df의 LSTM
3. df_short의 RNN
4. df_short의 LSTM
5. tr의 RNN
6. tr의 LSTM

각각의 실험 번호별로 1, 7, 14일 후의 서울시의 코로나19 추가 확진자 수 예측을 하는 실험을 진행했다.

# 파일 이름

## 코드

1~6번 실험은 1, 7, 14일로 구분하였으며, RNN과 LSTM 사용 여부는 파일 제목의 가장 앞에 지정하였다.

|  | 1일 | 7일 | 14일 |
| --- | --- | --- | --- |
| 1번 | rnn_1 | rnn_7 | rnn_14 |
| 2번 | lstm_1 | lstm_7 | lstm_14 |
| 3번 | rnn_short_1 | rnn_short_7 | rnn_short_14 |
| 4번 | lstm_short_1 | lstm_short_7 | lstm_short_14 |
| 5번 | rnn_tr_1 | rnn_tr_7 | rnn_tr_14 |
| 6번 | lstm_tr_1 | lstm_tr_7 | lstm_tr_14 |

## 데이터

| 1번 | 2번 | 3번 |
| --- | --- | --- |
| df.csv | df_short.csv | tr.csv |

# 요구사항

다음과 같은 소프트웨어가 요구된다.

- Pandas
- NumPy
- Matplotlib
- scikit-learn
- tqdm
- Pytorch
- (GPU 가속) Pytorch with CUDA
- (GPU 가속) NVIDIA 그래픽 드라이버

아래의 명령어를 통해 모두 설치가 가능하다.

Linux

`pip3 install pandas numpy matplotlib scikit-learn tqdm torch torchvision torchaudio`

Windows

`pip3 install pandas numpy matplotlib scikit-learn tqdm torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu117`

NVIDIA 그래픽 드라이버는 NVIDIA 홈페이지에서 받을 수 있다.
