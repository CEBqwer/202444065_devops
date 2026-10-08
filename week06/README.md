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
