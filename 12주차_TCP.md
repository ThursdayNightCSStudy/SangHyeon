# TCP
> TCP(전송 제어 프로토콜)는 네트워크의 장치 간에 안정적인 연결을 설정하는 데 사용되는 통신 프로토콜

TCP(전송 제어 프로토콜)는 네트워크의 장치 간에 안정적인 연결을 설정하는 데 사용되는 통신 프로토콜입니다. TCP는 오류 검사, 손실된 데이터의 재전송 및 흐름 제어를 포함하여 장치 간에 데이터를 전송하기 위한 일련의 규칙을 제공합니다.

## TCP에서 사용하는 연결 프로세스와 연결 해제 프로세스
### 3방향 핸드셰이크
> 두 장치를 연결하기 위한 프로세스

1. 첫 번째 장치(클라이언트)는 SYN(동기화) 패킷을 두 번째 장치(서버)로 보냅니다.
2. 두 번째 장치는 SYN-ACK(synchronize-acknowledge) 패킷으로 응답하여 SYN 패킷을 수신했음을 확인합니다.
3. 첫 번째 장치는 ACK(확인) 패킷을 두 번째 장치로 다시 보내 연결 설정 프로세스를 완료합니다.
3방향 핸드셰이크가 완료되면 설정된 TCP 연결을 통해 두 장치 간에 데이터를 전송할 수 있습니다.

### 4방향 핸드셰이크
> TCP에서 두 장치 간의 연결을 종료하기 위한 프로세스

1. 첫 번째 장치(클라이언트)는 FIN(완료) 패킷을 두 번째 장치(서버)로 보내 더 이상 보낼 데이터가 없음을 나타냅니다.
2. 두 번째 장치는 ACK 패킷으로 응답하여 FIN 패킷을 수신했음을 확인합니다.
3. 그런 다음 두 번째 장치는 더 이상 보낼 데이터가 없음을 나타내는 FIN 패킷을 첫 번째 장치로 보냅니다.
4. 첫 번째 장치는 ACK 패킷으로 응답하여 FIN 패킷을 수신했음을 확인합니다.

### SYN, ACK, FIN
SYN, ACK 및 FIN은 TCP 연결에서 다양한 기능을 제공하기 위해 TCP 헤더에서 사용되는 TCP 플래그 또는 제어 비트입니다.

SYN(동기화)은 TCP 3방향 핸드셰이크에서 연결을 시작하는 데 사용됩니다. 클라이언트는 서버와 연결을 원할 때 서버에 SYN 패킷을 보내 연결을 요청합니다. SYN 플래그는 패킷의 TCP 헤더에서 1로 설정됩니다.

ACK(Acknowledge)는 패킷이 수신되었는지 확인하는 데 사용됩니다. 장치가 ACK 플래그가 1로 설정된 패킷을 수신하면 패킷을 수신했음을 승인합니다. TCP 3방향 핸드셰이크에서 서버는 클라이언트의 SYN 패킷에 대한 응답으로 ACK 패킷을 클라이언트로 전송하여 서버가 클라이언트의 연결 설정 요청을 수신했음을 확인합니다.

FIN(완료)은 TCP 연결을 종료하는 데 사용됩니다. 장치가 TCP 연결을 닫으려는 경우 FIN 패킷을 다른 장치로 보냅니다. FIN 플래그는 패킷의 TCP 헤더에서 1로 설정됩니다. 상대 기기는 ACK 패킷으로 응답하여 FIN 패킷을 수신했음을 확인한 다음 자신의 FIN 패킷을 전송하여 연결 종료 프로세스를 완료합니다.

전반적으로 이러한 TCP 플래그 또는 제어 비트는 TCP 연결 설정 및 종료 중에 필요한 제어 및 동기화를 제공합니다.

### 패킷의 헤더에서 플래그가 1로 설정된다는 것
TCP(전송 제어 프로토콜) 패킷에서 "플래그가 1로 설정됨"은 TCP 헤더의 해당 제어 비트 또는 플래그가 활성화되거나 켜져 있음을 의미합니다.

TCP 헤더는 소스 및 대상 포트 번호, 시퀀스 및 승인 번호, 다양한 제어 비트 또는 플래그와 같은 TCP 연결에 대한 중요한 정보를 포함하는 패킷 섹션입니다. 각 플래그는 TCP 프로토콜의 특정 기능 또는 제어 작업에 해당합니다.

예를 들어, SYN(동기화) 플래그는 연결을 시작하기 위해 패킷의 TCP 헤더에서 1로 설정됩니다. ACK(승인) 플래그는 패킷 수신을 확인하기 위해 1로 설정됩니다. 연결을 종료하려면 FIN(종료) 플래그가 1로 설정됩니다.

패킷의 TCP 헤더에 적절한 플래그를 설정함으로써 장치는 연결 설정, 데이터 전송 및 연결 종료와 같은 TCP 연결의 다양한 측면을 제어하고 관리할 수 있습니다.

## 혼잡제어 흐름제어
> 전반적으로 TCP는 혼잡 제어 및 흐름 제어 메커니즘을 제공하여 네트워크를 통해 안정적이고 효율적이며 안전한 데이터 전송을 보장합니다.
### 혼잡제어
혼잡 제어는 네트워크 정체를 방지하고 데이터가 효율적으로 전송되도록 하기 위해 TCP에서 사용되는 메커니즘입니다. 네트워크가 처리할 수 있는 것보다 더 많은 데이터가 전송될 때 발생하며, 이로 인해 패킷 손실, 지연 및 네트워크 성능 저하가 발생할 수 있습니다. TCP는 혼잡 제어 메커니즘을 사용하여 혼잡이 감지되면 데이터 전송 속도를 낮추어 패킷 손실 위험을 줄이고 네트워크 성능을 향상시킵니다.

TCP는 느린 시작, 혼잡 방지, 빠른 재전송과 같은 다양한 혼잡 제어 알고리즘을 사용하여 네트워크의 데이터 흐름을 관리합니다.
- 느린 시작
    > 발신자가 적은 수의 패킷을 보내는 것으로 시작하여 네트워크 정체를 감지할 때까지 점차적으로 패킷 수를 늘립니다.
- 혼잡 방지
    > 발신자는 정체가 감지되면 네트워크의 피드백을 사용하여 전송 속도를 조정하여 패킷 전송 속도를 늦춥니다.
- 빠른 재전송
    > 발신자는 손실된 패킷을 신속하게 재전송하여 패킷 손실이 네트워크 성능에 미치는 영향을 줄입니다. 중복된 순번의 패킷을 3개 받으면 재전송합니다.

## 흐름 제어
흐름 제어는 데이터가 수신 장치에서 처리할 수 있는 속도로 전송되도록 하기 위해 TCP에서 사용되는 또 다른 메커니즘입니다. 
발신자와 수신자 간의 데이터 흐름 제어에 중점을 둡니다.
데이터가 너무 빨리 전송되면 수신 장치가 압도되어 모든 데이터를 처리하지 못할 수 있으므로 흐름 제어가 중요합니다. TCP는 슬라이딩 윈도우 메커니즘을 사용하여 데이터 전송 속도를 제어하고 수신 장치에서 받은 피드백을 기반으로 윈도우 크기를 조정합니다.

흐름 제어는 데이터 전송 속도를 관리하기 위해 TCP에서 사용되는 또 다른 메커니즘이지만  데이터가 너무 빨리 전송되면 수신 장치가 압도되어 모든 데이터를 처리하지 못할 수 있으므로 흐름 제어가 중요합니다.
- 슬라이딩 윈도우 메커니즘
    > 데이터 전송 속도를 제어하고 수신 장치에서 받은 피드백을 기반으로 윈도우 크기를 조정합니다. 발신자는 자신이 보낸 승인되지 않은 패킷 수를 추적하고 수신자의 창 크기에 따라 전송 속도를 조정합니다. 수신자의 창 크기는 주어진 시간에 처리할 수 있는 데이터의 양을 나타냅니다. 수신자의 창 크기가 작으면 송신자는 데이터 손실이나 지연을 방지하기 위해 데이터 전송 속도를 늦춥니다. 수신자의 창 크기가 큰 경우 송신자는 사용 가능한 네트워크 용량을 활용하기 위해 데이터 전송 속도를 높일 수 있습니다.

- Stop and Wait
    > 매번 전송한 패킷에 대해 확인 응답을 받아야만 그 다음 패킷을 전송합니다.

## 혼잡 제어와 흐름 제어의 차이
혼잡 제어는 호스트와 라우터를 포함한 보다 넓은 관점에서 데이터 전송 속도를 관리하여 네트워크 혼잡을 방지합니다.
흐름 제어는 송신자와 수신자 간의 데이터 흐름을 관리하여 데이터 손실을 방지하고 효율적인 네트워크 성능을 보장합니다.

## TCP의 사용
- 웹 검색
    > TCP는 웹 서버와 클라이언트 간의 HTTP(Hypertext Transfer Protocol) 통신에 사용되어 사용자가 웹을 검색하고 웹 페이지를 볼 수 있도록 합니다.
- 이메일
    > TCP는 메일 서버와 클라이언트 간의 SMTP(Simple Mail Transfer Protocol) 통신에 사용되어 사용자가 이메일을 보내고 받을 수 있도록 합니다.
- 파일 전송
    > TCP는 서버와 클라이언트 간의 FTP(파일 전송 프로토콜) 통신에 사용되며 사용자는 인터넷을 통해 파일을 전송할 수 있습니다.
- 원격 로그인:
    > TCP는 원격 호스트와 클라이언트 간의 텔넷 통신에 사용되어 사용자가 다른 컴퓨터에 원격으로 로그인하고 리소스에 액세스할 수 있도록 합니다.
- 보안 통신
    > TCP는 인터넷을 통해 클라이언트와 서버 간에 보안 통신을 제공하는 SSL/TLS(Secure Sockets Layer/Transport Layer Security) 프로토콜의 전송 계층으로 사용됩니다.
- 데이터베이스 액세스
    > TCP는 클라이언트와 데이터베이스 서버 간의 통신에 사용되어 사용자가 데이터베이스에 저장된 데이터에 액세스하고 관리할 수 있도록 합니다.
- VoIP(Voice over IP)
    > TCP는 VoIP 장치와 서버 간의 통신에 사용되어 사용자가 인터넷을 통해 음성 통화를 할 수 있도록 합니다.
    (국제 전화)