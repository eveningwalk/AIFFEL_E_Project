# AIFFEL Campus Online 4th Code Peer Review Templete
- 코더 : 남희정
- 리뷰어 : 이하영


# PRT(PeerReviewTemplate)
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.
- [x] 1.코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
- [x] 2.주석을 보고 작성자의 코드가 이해되었나요?

```Python
    threshold = 7 # 등장 빈도수의 th
    total_cnt = len(src_tokenizer.word_index) # 단어의 수
    rare_cnt = 0 # 등장 빈도수가 threshold보다 작은 단어의 개수를 카운트
    total_freq = 0 # 훈련 데이터의 전체 단어 빈도수 총 합
    rare_freq = 0 # 등장 빈도수가 threshold보다 작은 단어의 등장 빈도수의 총 합
```

- [x] 3.코드가 에러를 유발할 가능성이 있나요?
  <br>(없음)
- [x] 4.코드 작성자가 코드를 제대로 이해하고 작성했나요?
  
  ```Python
    Text Min 값 : 30 Text Max 값 : 40 Summary Min : 6 Summary Max : 8 ratio=0.35

    좀 더 성능을 높이기 위해 Min/Max 값의 폭을 넓혀서 다시 모델이 하였고, 상기 값들에 대한 예측결과는 Abstract Summarization의 경우는 큰 차이가 없었고, Extractive Summarization는 조금 더 정확한 문장      을 만든다는것을 확있했습니다.

    Text Min 값 : 25 Text Max 값 : 48 Summary Min : 5 Summary Max : 10 ratio=0.5

    보다 성능을 개선하기 위해 ratio=0.5로 올려 test을 진행했하였고, Extractive Summarization의 경우 0.35일때보다 성능이 향상되는것을 확인할 수 있었습니다.
  ```
  
- [ ] 5.코드가 간결한가요?

```Python
    from importlib.metadata import version
    import nltk
    import tensorflow
    import summa
    import pandas
    from bs4 import BeautifulSoup 

    print(nltk.__version__)
    print(tensorflow.__version__)
    print(pandas.__version__)
    print(version('summa'))
    import nltk
    nltk.download('stopwords')

    import numpy as np
    import pandas as pd
    import os
    import re
    import matplotlib.pyplot as plt
    from nltk.corpus import stopwords
    from bs4 import BeautifulSoup 
    from tensorflow.keras.preprocessing.text import Tokenizer 
    from tensorflow.keras.preprocessing.sequence import pad_sequences
    import urllib.request
    import warnings
    warnings.filterwarnings("ignore", category=UserWarning, module='bs4')
 ```
 되도록이면 불러오려는 모듈은 코드 첫 줄에 입력하고, 중복이 없는 것이 좋을 듯 합니다.
