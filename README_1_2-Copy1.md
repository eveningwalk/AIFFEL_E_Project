# AIFFEL_E_Project

<aside>
🔑 **PRT(Peer Review Template)**

- [○]  1.코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
- [○]  2.주석을 보고 작성자의 코드가 이해되었나요?
    
    def gradient(X, W, b, y):
        N은 데이터 포인트의 개수
        N = len(y)
    
    y_pred 준비
        y_pred = model(X, W, b)
    
    공식에 맞게 gradient 계산
        dW = 1/N * 2 * X.T.dot(y_pred - y)
        
    b의 gradient 계산
        db = 2 * (y_pred - y).mean()
        return dW, db
    
- [○]  3.코드가 에러를 유발할 가능성이 있나요?
    
    csv_path = os.getenv("HOME") + "/aiffel/bike-sharing-demand/bike-sharing-demand/train.csv"
    코드 실행 환경에 따라 데이터의 경로를 지정해주어야 할 필요가 있습니다.
    
- [○]  4.코드 작성자가 코드를 제대로 이해하고 작성했나요? (직접 인터뷰해보기)
    
    data = pd.read_csv(csv_path, index_col=0, parse_dates=True)
    제 코드와 비교하였을 때 크게 다른 부분 중 하나가 이 부분이었습니다.
    이후 코드의 to_datetime() 메서드를 이용하는 부분에서 위 코드가 존재하냐에 따라 메서드를 사용하는 방식이 달라질 수 있음을 알게 되었습니다.
    
- [X]  5.코드가 간결한가요?
    
    plt.figure(figsize=(15,13))

    plt.subplot(2, 3, 1) 
    sns.countplot(x = 'year', data = new_data)

    plt.subplot(2, 3, 2) 
    sns.countplot(x = 'month', data = new_data)

    plt.subplot(2, 3, 3) 
    sns.countplot(x = 'day', data = new_data)

    plt.subplot(2, 3, 4) 
    sns.countplot(x = 'hour', data = new_data)

    plt.subplot(2, 3, 5) 
    sns.countplot(x = 'minute', data = new_data)

    plt.subplot(2, 3, 6) 
    sns.countplot(x = 'second', data = new_data)
    
    서브플롯을 행렬로 설정하면 코드를 줄일 수 있습니다.
    예시)
    fig, axes = plt.subplots(2, 3, figsize=(15, 10))
    sns.countplot(data=train, x='year', ax=axes[0, 0])
    sns.countplot(data=train, x='month', ax=axes[0, 1])
    sns.countplot(data=train, x='day', ax=axes[0, 2])
    sns.countplot(data=train, x='hour', ax=axes[1, 0])
    sns.countplot(data=train, x='minute', ax=axes[1, 1])
    sns.countplot(data=train, x='second', ax=axes[1, 2])
    
</aside>
