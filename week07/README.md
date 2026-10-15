## docker compose ps
<pre>
  <code>
  % docker compose ps
  NAME                IMAGE            COMMAND                   SERVICE   CREATED          STATUS                    PORTS
  guestbook-redis-1   redis:7-alpine   "docker-entrypoint.s…"   redis     50 seconds ago   Up 49 seconds (healthy)   6379/tcp
  guestbook-web-1     guestbook-web    "python app.py"           web       50 seconds ago   Up 44 seconds (healthy)   0.0.0.0:8080->5000/tcp, [::]:8080->5000/tcp
  </code>
</pre>

## scale 후 웹 컨테이너 호스트명
<img width="302" height="64" alt="image" src="https://github.com/user-attachments/assets/5f95bea2-e4eb-47ef-ae65-45cae4cf95e1" />

<img width="308" height="64" alt="image" src="https://github.com/user-attachments/assets/207e61ae-cd74-4ab7-afc6-2caaa14e4d96" />

<img width="298" height="56" alt="image" src="https://github.com/user-attachments/assets/636e95ac-a308-43fd-8bcf-0ee4bcf0acdd" />

<pre>
  <code>
  % docker ps --format "{{.ID}} {{.Names}}"
  161910e94eec guestbook-web-3
  dffcf0817340 guestbook-web-2
  cf770f20e1ac guestbook-nginx-1
  086a8a145654 guestbook-web-1
  dc90e9f7cc8a guestbook-redis-1
  </code>
</pre>

## down 후 up VS down -v 후 up
- down 후 up : 컨테이너와 네트워크만 지움, 데이터 남음 -> 방명록 글 남아있음
- down -v 후 up : 볼륨까지 지움, 데이터 사라짐 -> 방명록 글도 사라짐

## .env는 왜 Git에 올리지 X?
- .env 파일에는 DB 비밀번호, API 키 등 외부에 공개되면 안되는 민감한 정보
- Git에 커밋하면 Github 저장소와 커밋 기록을 통해 비밀 정보가 노출될 위험이 있으므로 X
