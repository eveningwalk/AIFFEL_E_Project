
# Code Peer Review 
--------
- 코더 : 남희정
- 리뷰어 : 박재영
# PRT(Peer Review)
--------
각 항목을 스스로 확인하고 체크하고 확인하여 작성한 코드에 적용하세요  

[ ] 1. 코드가 정상적으로 동작하고 주어진 문제를 해결했나요  
[O] 2. 주석을 보고 작성자의 코드가 이해되었나요?  
[O] 3. 코드가 에러를 유발한 가능성이 있나요?  
[O] 4. 코드 작성자가 코드를 제대로 이해하고 작성했나요?  
[O] 5. 코드가 간결한가요?  

# 참고링크 및 코드 개선 여부 
----------
1.코드가 정상적으로 동작하고 주어진 문제를 해결했나요  
  - 기본적인 기능 구현은 잘되어 있고, 정상적으로 동작합니다.
  - 다만, *각도, 거리, 음영* 등 다양한 조건과 사진에서 기능 동작을 확인했다면 
  - 더 좋은 코드 페이지가 될 것 같습니다. 

2.주석을 보고 작성자의 코드가 이해되었나요? 
   - 각 코드 블록 마다, line by line 으로 주석 처리가 되어 있어 해석하기 좋았습니다.
   - ex)
          list_landmarks = []
          # 랜드마크의 위치를 저장할 list 생성    

          # 얼굴 영역 박스 마다 face landmark를 찾아냅니다
          # face landmark 좌표를 저장해둡니다
          for dlib_rect in dlib_rects:
              points = landmark_predictor(img_rgb, dlib_rect)
                  # 모든 landmark의 위치정보를 points 변수에 저장
              list_points = list(map(lambda p: (p.x, p.y), points.parts()))
                  # 각각의 landmark 위치정보를 (x,y) 형태로 변환하여 list_points 리스트로 저장
              list_landmarks.append(list_points)
                  # list_landmarks에 랜드마크 리스트를 저장


          print(len(list_landmarks[0]))
              # 얼굴이 n개인 경우 list_landmarks는 n개의 원소를 갖고
              # 각 원소는 68개의 랜드마크 위치가 나열된 list 

3.코드가 에러를 유발할 가능성이 있나요?
    - 없어보입니다.  
    
4.코드가 간결한가요?  
    - 코드 문법이 간결해서, 읽기 좋은 구조를 가지고 있습니다.  
    - 다만, 저도 잘 안지키는 부분이긴 한데  
    - 파이썬 코드 컨벤션(PEP) :  https://spoqa.github.io/2012/08/03/about-python-coding-convention.html  
    - 울 참조하시면, 더 좋은 코드 페이지가 될 것 같습니다.  

