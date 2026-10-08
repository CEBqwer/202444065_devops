## 내 이미지 주소
ghcr.io/cebqwer/guestbook

## 친구 이미지 실행 로그
<pre>
  <code>
  % docker run -d -p 8081:5000 --name idgb ghcr.io/makyraen/inhatc-devops-guestbook:v1
    b6eb2c77d84869c424b35b3954d310bab1d271fa91273d64efd75c5aa7947cbf
  % docker logs idgb
    [INFO] REDIS_HOST 없음 → 메모리 모드로 동작합니다.
    [INFO] InhaTC DevOps 방명록 시작 — http://0.0.0.0:5000
     * Serving Flask app 'app'
     * Debug mode: off
    WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
     * Running on all addresses (0.0.0.0)
     * Running on http://127.0.0.1:5000
     * Running on http://172.17.0.4:5000
    Press CTRL+C to quit
  </code>
</pre>

## Dockerfile
<pre>
  <code>
    FROM python:3.12-slim

    # 작업 디렉터리 설정
    WORKDIR /app

    # COPY : 파일을 이미지 안으로 복사
    COPY requirements.txt .

    # 빌드할 때 실행할 명령
    RUN pip install requirements.txt

    COPY . .

    # 환경 변수 설정
    ENV APP_TITLE="CEBqwer 방명록" \
        THEME_COLOR="#89b586"

    # 포트 번호 (어떤 포트를 사용할 건지 알려주기만, 실제로 열리지 X)
    EXPOSE 5000

    # 컨테이너 시작할 때 실행할 명령
    CMD ["python", "app.py"]
  </code>
</pre>

## 빌드 캐시 동작 로그 (CASHED)
<pre>
  <code>
  => transferring context: 3.24kB                                                         0.0s
  => CACHED [2/6] WORKDIR /app                                                               0.0s
  => CACHED [3/6] COPY requirements.txt .                                                    0.0s
  => CACHED [4/6] RUN pip install —no-cache-dir -r requirements.txt                         0.0s
  => [5/6] COPY . .                                                                          0.0s
  => [6/6] RUN useradd -m appuser 
  </code>
</pre>
