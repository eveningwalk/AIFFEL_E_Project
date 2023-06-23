# AIFFEL Campus Online 4th Code Peer Review Templete
- 코더 : 남희정
- 리뷰어 : 소용현
# AIFFEL_E_Project

<aside>
🔑 **PRT(Peer Review Template)**

- [O]  1.코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
- [O]  2.주석을 보고 작성자의 코드가 이해되었나요?
- [o]  3.코드가 에러를 유발할 가능성이 있나요?
```
sentence = re.sub(r'[^A-Za-z0-9가-힣],!?]', " ", sentence)  #hjnam [Your Code]
```
정규표현식을 사용하는 경우 직접적인 에러가 없더라도 의도한 정규표현식이 제대로 작동하지 않을 수 있으니, 코드 작성 후에 확인을 해보시면 좋을 것 같습니다.
    
- [O]  4.코드 작성자가 코드를 제대로 이해하고 작성했나요? (직접 인터뷰해보기)
- [x]  5. 코드가 간결한가요?
```
data_path = os.getenv('HOME')+ '/aiffel/transformer_chatbot/data/'
file_path = os.path.join(data_path,os.listdir(data_path)[1] )
data = pd.read_csv(file_path, encoding='UTF-8')
```
```
# 질문과 답변의 쌍인 데이터셋을 구성하기 위한 데이터 로드 함수
def load_conversations() : 
  with open(file_path, errors='ignore') as file:
    lines = file.readlines()
    
  for line in lines:
    parts = line.replace('\n', '').split(' +++$+++ ')

  q, a = [], []
  with open(file_path, 'r') as file:
    lines = file.readlines()[1:]
    for line in lines:
        split_line = line.split(',')
        q.append(preprocess_sentence(split_line[0]))
        a.append(preprocess_sentence(split_line[1]))
  return q, a    
```
데이터를 pandas를 이용해 로딩했는데, 다시한번 파일을 불러 csv를 파싱하는 함수를 선언하고 호출하였다.  
불필요한 작업 대신 data에 반복문을 화용해서 question, answer를 만들면 좋을 것 같습니다.  
with open(file_path, errors='ignore') as file:
    lines = file.readlines()  
for line in lines:
    parts = line.replace('\n', '').split(' +++$+++ ')
필요없는 코드는 제거하는 것이 좋을 것 같습니다.

</aside>
