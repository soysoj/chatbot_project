🔑 **PRT(Peer Review Template)**
배운점: 트랜스포머의 구조를 더 자세히 배울 수 있었고, 트랜스포머 구조를 배우면서 이전에 배웠던 부분들도 복습할 수 있어서 너무 도움이 됐습니다.  
아쉬운 점: 결과가 계속 한단어로만 나와서 너무 아쉬웠고, 아직도 그것을 고칠 수 없어서 너무 아쉬웠습니다. 그리고 맞춤법 검사기를 쓰고 싶었지만 아쉽게도 계속 오류가 떠서 제대로 할 수 없었던게 아쉬웠습니다.   
느낀 점: 트랜스포머의 구조를 제대로 배울 수 있었고, 한 단어만 나오는 해결책을 찾으면서 다른 방법의 생성 디코딩이 있다는 사실을 알게되어 좋았습니다.  
어려웠던 점: 한단어로만 나오는 문제를 아직도 해결할 수 없어서 어려웠습니다.  
____________________________________________________________________________________________________
- [x]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요? (완성도)**
    - 문제에서 요구하는 최종 결과물이 첨부되었는지 확인
    - 문제를 해결하는 완성된 코드란 프로젝트 루브릭 3개 중 2개, 
    퀘스트 문제 요구조건 등을 지칭
        - 해당 조건을 만족하는 부분의 코드 및 결과물을 캡쳐하여 사진으로 첨부
          1. 전처리
             ![image](https://github.com/4rldur0/chatbot_project/assets/111371565/4814808a-1a18-4ba6-9a51-0c8c46eddfb9)

          2. 모델 구현
              ![image](https://github.com/4rldur0/chatbot_project/assets/111371565/484023a3-37d7-4cd0-ac51-0b2220ac26a9)

          3. 학습
             ![image](https://github.com/4rldur0/chatbot_project/assets/111371565/385222d4-6368-4533-92dd-5be47ffe6f57)

          4. 추론
            ![image](https://github.com/4rldur0/chatbot_project/assets/111371565/98ba362b-251f-4134-a2b8-6beba2520b7a)


- [ ]  **2. 프로젝트에서 핵심적인 부분에 대한 설명이 주석(닥스트링) 및 마크다운 형태로 잘 기록되어있나요? (설명)**
    - [ ]  모델 선정 이유
    - [ ]  Metrics 선정 이유
    - [ ]  Loss 선정 이유

- [x]  **3. 체크리스트에 해당하는 항목들을 모두 수행하였나요? (문제 해결)**
    - [ ]  데이터를 분할하여 프로젝트를 진행했나요? (train, validation, test 데이터로 구분)
          ```
           BATCH_SIZE = 64
            BUFFER_SIZE = 20000
            
            # 디코더는 이전의 target을 다음의 input으로 사용합니다.
            # 이에 따라 outputs에서는 START_TOKEN을 제거하겠습니다.
            dataset = tf.data.Dataset.from_tensor_slices((
                {
                    'inputs': Q,
                    'dec_inputs': A[:, :-1]
                },
                {
                    'outputs': A[:, 1:]
                },
            ))
            
            dataset = dataset.cache()
            dataset = dataset.shuffle(BUFFER_SIZE)
            dataset = dataset.batch(BATCH_SIZE)
            dataset = dataset.prefetch(tf.data.experimental.AUTOTUNE)
            print("슝=3")
            ```
      
           > test dataset은 필요하지 않음
    - [x]  하이퍼파라미터를 변경해가며 여러 시도를 했나요? (learning rate, dropout rate, unit, batch size, epoch 등)   
          > Max_length: 12, Epoch: 10 / Max_length: 12, Epoch: 50 / Max_length: 20, Epoch: 50 / Max_length: 40, Epoch: 50 와 같이 하이퍼파라미터를 변경하며 더 나은 결과값을 찾으려고 함
    - [x]  각 실험을 시각화하여 비교하였나요?  
          > 각 추론 결과를 디코딩하여 비교
          ![image](https://github.com/4rldur0/chatbot_project/assets/111371565/fefe3ad4-b2bc-4169-ac67-154afe322a57)

    - [x]  모든 실험 결과가 기록되었나요?  
          > 추론 결과가 잘 나오지 않는 것에 대해 다양한 방법으로 시도했음
           ![image](https://github.com/4rldur0/chatbot_project/assets/111371565/ef5246af-1c80-41ea-9639-ea39a49d8d41)

           > decoder_inference()에서 predicted_id를 확인해봤을 때, 만약 모델이 두 번째 토큰으로 항상 END_TOKEN을 반환하지 않는지 확인해보면 좋을 것 같습니다


- [x]  **4. 프로젝트에 대한 회고가 상세히 기록 되어 있나요? (회고, 정리)**
    - [x]  배운 점
    - [x]  아쉬운 점
    - [x]  느낀 점
    - [x]  어려웠던 점
