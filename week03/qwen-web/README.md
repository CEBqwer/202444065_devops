# 3주차

## 오늘 배운 내용

1. 자동화의 필요성
2. Qwen, Ollama
   - Qwen : 알리바바 클라우드에서 개발한 대형 언어 모델
   - Ollama : 로컬 환경에서 LLM을 쉽게 설치, 실행할 수 있게 해주는 오픈소스 플랫폼   
   <pre>
     <code>
       $ cd ~
       $ cd devops
       $ cd week03
       $ cd qwen-web
       $ python3 chat.py
     </code>
   </pre>
   <img width="1211" height="504" alt="image" src="https://github.com/user-attachments/assets/194df767-cb50-4acb-8eef-e0538a8df36b" />
  며칠이 지나도 경로, 파이썬 파일을 기억해서 실행할 수 있을까... ==> 자동화

3. 셸 스크립트 작성 및 실행
   - 참고
     <pre>
       <code>
         # permission denied
         # 실행 권한 설정
         chmod u+x <파일 이름.sh>

         # Command not found
         ./<파일 이름.sh>
       </code>
     </pre>
   - 셔뱅 (shebang)
     - #!
     - 어떤 인터프리터로 실행할지 OS에 알려주는 부분, 파일의 첫 줄에 작성
   - start.sh
     <pre>
       <code>
          cd "$(dirname "$0")" || exit 1 
       </code>
     </pre>
       - **exit 1**   
         - 리눅스 명령어는 성공 또는 실패 값 남김   
         명령 종료 상태 성공 : 0   
         명령 종료 상태 실패 : 0 이외
         - cd 성공하면   
           exit status = 0 -> True
         - 존재하지 않는 디렉터리면   
           exit status = 1 -> False
     <pre>
       <code>
          if ! command -v python3 >/dev/null 2>&1; then
       </code>
     </pre>
      - **command -v**
        - 명령어를 실행할 수 있으면, 어느 경로에 있는지 확인
        - 없는 명령어라면, 아무것도 출력 X, 실패 상태 반환
        <pre>
          <code>
            $ command -v python3
            /usr/bin/python3      # python3이 있는 경로
            $ echo $?             # 종료 코드 출력
            0                     # 정상 종료
          </code>
        </pre>
      - **>/dev/null**
        - 표준 출력을 /dev/null(리눅스의 일종의 쓰레기통)로 보내기   
        = 출력을 버림
      - **2>&1**
        - 2번 표준 오류를 1번 표준 출력이 가는 곳(/dev/null)로 보내기
