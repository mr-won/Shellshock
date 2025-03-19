# Shellshock
Shellshock

Payload
GET /cgi-bin/test.cgi HTTP/1.1
Host: 172.16.1.30
User-Agent: () { :; }; /bin/bash -c "echo hacked > /tmp/shellshock"

- 공격 이름: `Shellshock`
- 판단 근거: `User-Agent` 헤더에 `() { :; };` 와 같이 함수 정의를 시도하고, 이어서 `/bin/bash` 명령어를 실행하는 것이 Shellshock 공격의 특징입니다.
- 탐지 패턴: `User-Agent: \(\) { :; };`
- 설명: Shellshock은 Bash 쉘의 취약점을 악용하는 공격으로, 공격자가 특수하게 조작된 환경 변수를 통해 임의의 코드를 실행할 수 있게 합니다.
- 대응 방법: 웹 서버 및 클라이언트의 Bash 쉘을 최신 버전으로 업데이트해야 합니다. WAF (Web Application Firewall)에서 `User-Agent` 헤더에 `() { :; };` 패턴을 탐지하고 차단하는 규칙을 설정합니다.
