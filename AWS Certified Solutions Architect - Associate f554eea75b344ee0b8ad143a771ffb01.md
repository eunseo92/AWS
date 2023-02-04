# AWS Certified Solutions Architect - Associate

# AWS 시작하기

1. AWS Budgets(예산)
    - 예산을 지정하여 비용과 사용량을 추적하는 서비스
    - 비용 또는 사용량이 사용자가 지정한 임계값을 초과 할 때 이메일 등으로 알림을 받거나 RDS/EC2 등의 서비스를 중지하는 작업을 연결할 수 있음
    - 비용할당 태그를 이용해 AWS 특정 리소스에 태그 값을 지정하여 태그에 대한 리소스 보고서만 생성 가능
    
   
2. AWS Cost Explorer(비용 탐색기)
    - AWS 서비스에 대한 비용 및 사용량을 분석하는 서비스
    - 서비스별, 계정별로 일별, 월별 사용량 및 비용을 확인하여 보고서를 생성 및 다운로드 할 수 있음
    - Cost Explorer는 그래프, 숫자를 통한 시각화 된 인터페이스를 제공
    
 
   
    
3. 글로벌 인프라
    
    ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%204.png)
    
    1. 리전(Region)
        - 데이터 센터를 클러스터링 하는 물리적 위치
        - 1개 AWS 리전 = 2개이상의 가용영역으로 구성
    2. 가용영역(Availability Zone - AZ)
        - 가용영역 = 하나 이상의 개별 데이터 센터
        - 가용영역끼리는 물리적으로 떨어져 있고, 고속 네트워크로 연결됨
        - 고가용성 설계 = 다중 AZ(Multi-AZ), 2개 이상의 가용영역에 시스템 배치
    3. 엣지 로케이션(Edge Location)
        - 엣지 로케이션에 콘텐츠(데이터)를 캐싱하여 사용자에게 더 짧은 지연 시간으로 콘텐츠 전송
        - 글로벌 배포서비스인 AWS CloudFornt, Global Accelerator에서 대표적으로 사용
        
        ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%205.png)
        
    
    ### 리전-가용영역 예시(EC2)
    
    ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%206.png)
    

# Identity and Access Management(IAM)

- AWS 계정 및 권한 관리 서비스
    - AWS 서비스와 리소스에 대한 액세스 관리
    - 사용자, 그룹, 역할, 정책으로 구성
    - 리전에 속하는 서비스가 아닌 글로벌 서비스
    - 계정 보안 강화를 위해
        - 루트 계정(AWS회원가입시 만들어지는 계정)은 최초 사용자 계정 생성 이후 가능하면 사용하지 말 것
        - 사용자 계정(IAM 계정)으로 서비스를 사용하고 사용자는 필요한 최소한의 권한만 부여(최소권한의 원칙)
        - 루트계정과 개별 사용자 계정에 강력한 암호 정책과 멀티팩터 인증(MFA) 적용
        - 사용자의 암호에 대한 복잡성 요구 사항과 의무 교체 주기를 정의
    
    ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%207.png)
    


- IAM - 정책
    - AWS 리소스에 대한 액세스 권한을 정의한 것
    - 사용자, 그룹, 역할에 정책을 연결하여 사용
    - JSON 문서 형식으로 이루어짐
    - 정책이 명시되지 않는 경우 기본적으로 모든 요청이 거부(Deny)됨
    
    ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2016.png)
    
    ### JSON 정책 구문 예시
    
    ```json
    {
        "Version": "2012-10-17",
        "Statement": [
            {
                "Effect": "Allow",
                "Action": "ec2:Describe*",
                "Resource": "*"
            }, //EC2의 모든 리소스에 대해 읽기 권한 허용
            {
                "Effect": "Allow",
                "Action": "elasticloadbalancing:Describe*",
                "Resource": "*"
            }, //ELB의 모든 리소스에 읽기 권한 허용
            {
                "Effect": "Allow",
                "Action": [
                    "cloudwatch:ListMetrics",
                    "cloudwatch:GetMetricStatistics",
                    "cloudwatch:Describe*"
                ],
                "Resource": "*"
            }, //CloudWatch의 읽기 권한 허용
            {
                "Effect": "Allow",
                "Action": "autoscaling:Describe*",
                "Resource": "*"
            } //EC2 Auto Scaling에 읽기 권한 허용
        ]
    }
    ```
    
- IAM - 권한 경계 (Permission Boundary)
    - IAM 사용자 또는 역할에 최대 권한을 제한 하는 기능
    - AWS 전체 권한을 가지고 있어도 권한 경계에 대한 권한 범위로 축소되어 적용 됨
    
    ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2017.png)
    
    ### IAM 권한경계 실습
    
    1. 권한 추가(기존 정책 직접 연결)
    
    [https://www.notion.so](https://www.notion.so)
    
    1. EC2FullAccess 권한 선택 및 연결
        
        ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2018.png)
        
    2. IAM 사용자로 로그인 하여, EC2가 아닌 다른 서비스 선택
        
        ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2019.png)
        
    3. 권한이 없는 경우 액세스 불가
        
        ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2020.png)
        
    
    1. 권한 경계 설정(EC2ReadOnlyAcess 적용)
        
        ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2021.png)
        
    2. EC2ReadOnlyAccess 권한 선택
        
        ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2022.png)
        
    3. 권한 경계 설정 후 FullAccess와 ReadOnlyAccess의 권한경계인 ReadOnlyAccess만 적용
        
        ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2023.png)
        
        ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2024.png)
        
    
- IAM -역할
    - AWS 리소스에서 사용하는 자격증명
    - 특정 AWS 서비스가 다른 AWS 서비스에 액세스 하여 작업을 수행할 때 필요한 권한
    - 정책을 연결하여 IAM 역할에 작업 수행에 필요한 권한을 부여
    - EC2에서 실행되는 애플리케이션이 S3와 RDS 액세스 권한이 필요할 때 역할 사용
    
    ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2025.png)
    
- IAM -역할(신뢰정책)
    - IAM 역할을 사용하여 AWS 계정간 액세스 권한 위임을 하는 기능
    - 신뢰정책(Trust Policy)를 사용하여 다른 AWS 계정에 역할을 위임할 수 있음
    
    ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2026.png)
    

# 컴퓨팅

1. EC2 (Amazon Elastic Compute Cloud)
- AWS 클라우드 컴퓨팅 서비스 = 클라우드 가상 서버(Virtual Machin)
- EC2 클라우드 가상 서버를 “인스턴스” 라고 부름
- EC2 원격 접속 방법
    - Secure Shell Protocol(SSH)를 사용한 연결 → public key와 private key를 이용해 접속
    - 원격 데스크톱 프로토콜(RDP)를 사용한 연결 → 아이디, 패스워드를 이용해 접속 (윈도우 전용)
    - EC2 Instance Connect를 사용한 연결 (리눅스)
    - AWS Systems Manager 세션 관리자(Session Manager)를 사용한 연결
- 인스턴스 구매 옵션
    - 온디맨드 인스턴스 (On-Demand Instance)→ 약정 없이 초당 사용한 만큼 비용 지불
        - 단기간 동안 예측할 수 없는 워크로드 및 중단되어서 안되는 애플리케이션에 적합
        - EC2에서 처음으로 개발 중이거나 시험 중인 애플리케이션 사용에 적합
    - 스팟 인스턴스 → 사용 안하는 인스턴스를 경매 방식으로 구매하여 사용
        - 경매 조건에 미달하면 인스턴스가 정지 또는 종료 되므로 언제든지 시작 및 종료가 가능한 경우에 사용
        - 언제든 인스턴스가 종료될 수 있기 때문에 서버가 중단없이 지속적으로 실행 되어야 하는 경우 사용
        - 예약인스턴스 + 스팟인스턴스(짧은 시간 급격하게 증가된 용량이 필요한 경우)의 조합으로 사용
        - 사용하지 않는 예비 EC2용량을 경매방식으로 구매하여 사용하는 방식
    - 예약 인스턴스(Reserved Instance) → 1년 또는 3년 기간을 약정하여 인스턴스를 사용
        - 수요가 꾸준하고 예측가능한 경우에 유용
        - 결제옵션은 전체 선결제, 부분 선결제, 선결제 없음 3가지 선택 가능
        - 선택가능한 예약 인스턴스 유형
            - 표준 예약 인스턴스(Standard Reserved Instances): 인스턴스 타입을 지정하면 예약기간동안 변경 불가능(가장 저렴)
            - 전환형 예약 인스턴스(Convertible Reserved Instances): 예약기간동안 인스턴스 타입 변경가능
            - 정기 예약 인스턴스(Scheduled Reserved Instances): 지정된 시간, 날짜 동안에 인스턴스가 시작되어 사용(반복적이
            며 하루, 한 주 또는 한달의 일부 기간 동안 필요한 경우 적합)
    - Saving Plan → 1년 또는 3년 기간의 일정 사용량을 약정하여 시간당 요금으로 인스턴스를 사용
        - EC2 뿐만 아니라, Lambda 및 Fargate 서비스도 사용 가능
        - 예약인스턴스와 달리 EC2 인스턴스 패밀리, 인스턴스 사이즈, 리전, OS 관계 없이 적용 및 변경 가능한 유연성 있음
    - 전용 호스트/전용 인스턴스 → 전용 물리적 서버를 할당 받아서 인스턴스를 사용
        1. 전용호스트
            - CPU 소켓, 코어 등이 표시
            - CPU 코어나 물리적 서버에 할당되는 라이선스를 기존에 보유한 경우에 적합
        2. 전용 인스턴스
            - 전용 호스트에서 사용가능한 CPU 코어, 인스턴스 배치, 사용자 라이선스 사용 불가
- 인스턴스 유형
    - 인스턴스를 생성할 때 지정하는 유형에 따라 컴퓨터의 하드웨어가 결정
    - 인스턴스 유형은 CPU, 메모리, 스토리지 및 네트워킹 용량의 여러 조합으로 구성
    - 인스턴스 유형은 목적에 따라 범용, 컴퓨팅 최적화, 메모리 최적화, 가속화된 컴퓨팅, 스토리지 최적화의 인스턴스 패밀리로 분류 됨
    
- Elastic Network Interface(ENI)
    - 가상 네트워크 인터페이스
    - 인스턴스에 연결되어 네트워크 통신을 하는 역할
    
    ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2027.png)
    
- 보안그룹 (Security Group)
    - EC2 인스턴스에 대한 인바운드 및 아웃바운드 트래픽을 제어하는 인스턴스 수준의 방화벽
    - EC2인스턴스의 ENI와 연결됨
    - 보안 그룹은 연결 상태를 추적하는 상태저장 방화벽(Stateful Firewall)
    - 보안그룹은 허용규칙만 지정 가능하고 거부 규칙은 지정할 수 었음
    
    ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2028.png)
    
    *인바운드 트래픽 : 외부에서 EC2 인스턴스로 들어오는 트래픽
    
    *아웃바운드 트래픽 : EC2인스턴스에서 외부로 나가는 트래픽
    
    - 제어규칙
        - 트래픽 유형 (예, SSH, HTTP 등)
        - 프로토콜 (TCP, UDP 등)
        - 포트 (예, SSH 22, HTTP 80, HTTPS 443, MySQL 3306 등)
        - 대상 (개별 IP 주소, IP주소대역, 다른 보안 그룹 )
    
    ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2029.png)
    
- Security Group(보안그룹) - Stateful(상태저장)
    - 아웃바운드 규칙에 상관 없이, 허용된 인바운드 트래픽에 대한 반응으로 외부로 나가는 흐름이 수행
    
    ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2030.png)
    
    - 사용자가 인스턴스에서 요청을 전송하면 해당 요청의 응답 트래픽은 인바운드 보안 그룹 규칙에 관계없이 인바운드 흐름이 허용
    
    [https://www.notion.so](https://www.notion.so)
    
- 배치그룹
    - EC2 인스턴스 배치를 구성하는 방법
    
    ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2031.png)
    
    - 클러스터(Cluster) 배치그룹
        - 근접한 서버를 고속 네트워크로 연결하여 그룹화
        - 네트워크 지연시간이 매우 짧음
        - 짧은 대기시간이 필요한 고성능 컴퓨팅(HPC)등에 적합
    - 파티션(Partition) 배치그룹
        - 하드웨어를 파티션으로 그룹화
        - 파티션끼리는 서로 다른 하드웨어 사용(하드웨어 공유를 하지 않음)
        - 하나의 하드웨어 장애 발생 시 다른 하드웨어에 영향이 없음(파티션간 장애의 영향을 분리가능)
        - 하둡 등의 빅데이터 분산처리 시스템에 사용
    - 분산형(Spread) 배치그룹
        - 같은 서버랙의 서버를 그룹화
        - 분산그룹의 서버는 다른 서버랙에 있음
        - 분산그룹끼리 서버랙을 공유하지 않으므로 서버랙 장애 발생시 안전
        - 매우 중요하고 고가용성이 핑료한 애플리케이션에 적합
- EC2 라이프 사이클
    - 인스턴스 상태
        - 시작(Start) : 인스턴스 전원을 켜는 것
        - 재부팅(Reboot) : 인스턴스를 재부팅
        - 중지(Stop) : 인스턴스 전원을 끄는 것
        - 종료(Terminate) : 인스턴스 삭제
        - 최대절전모드(Hibernate) : RAM에 있는 애플리케이션 상태를 저장 후 중지상태 전환 (ex. 노트북에서 종료를 안하고 스크린만 닫을 때와 동일)
            
            서버 부팅 시 프로세스 로드시간이 오래 걸리는 시스템의 경우 유용
            
- EC2 스토리지
    1. Elastic Block Store(EBS)
        - EC2에 연결하여 사용하는 블록 스토리지
        - 여러 개의 EBS 볼륨을 생성하여 EC2에 추가 연결 가능
    2. Amazon Machine Image(AMI)
        - OS, 애플리케이션, 서버 프로그램 설정 등이 미리 구성된 이미지
        - EC2 인스턴스를 시작하는데 AMI 사용하여 EC2 시작 시 OS 설치나 서버 소프트웨어 설정 등을 별도로 할 필요 없음
    3. EC2 Image Builder
        - Amazon EC2 및 온프레미스에서 사용할 Linux 또는 Window 이미지의 생성, 유지 관리, 검증, 공유 및 배포를 간소화 하는 서비스
        
        ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2032.png)
        
    4. Instance Store
        - 블록 수준의 임시 스토리지
        - 임시 파일을 보관하는 가장 빠른 성능의 저장 옵션
        - EC2 인스턴스가 종료되면 데이터가 삭제 되므로 영구적인 저장소가 아닌 고성능을 요구하는 애플리케이션의 임시저장소로 적합
    5. Elastic File System(EFS)
        - 리눅스 환경의 EC2 인스턴스에서 연결하기 위한 네트워크 파일 스토리지
        - Network File System(NFS) 프로토콜을 지원
        
        ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2033.png)
        
        - 성능 및 스토리지 클래스
            - 스토리지 클래스
                - 표준 스토리지(Standard) - 3개의 가용영역에 데이터 저장, 자주 엑세스 하는 파일을 저장하는 데 사용
                - 표준 IA (Standard infrequent Access) - 3개의 가용영역에 데이터 저장, 자주 액세스 하지 않는 파일을 저장하는데 사용
                - One Zone - 1개의 가용영역에 데이터 저장, 자주 액세스하는 파일을 저장하는 데 사용
                - One Zone IA (One Zone Infrequent Access) - 1개의 가용영역에 데이터 저장, 자주 액세스하지 않는 파일을 저장하는 데 사용
                - EFS 수명주기 관리 정책 또는 EFS 지능형 계층화(Intelligent-Tiering)을 사용해 자주 사용하지 않는 데이터를 다른 스토 리지 클래스로 자동 전환 가능
            - **성능 모드**
                - ****I/O, 읽기 쓰기 속도 • 기본 범용 성능 모드 (General Purpose performance mode) – 일반적인 I/O 성능
                - 최대 I/O 성능 모드 (Max I/O performance mode) – 높은 성능의 처리가 필요한 빅데이터 분석 애플리케이션 등에 사용
                

# ELB(Elastic Load Balancer)

- Load Balancer 개요
    - 트래픽을 분산하는 서비스
    - EC2 인스턴스, 컨테이너, IP주소 등 여러 대상으로 자동으로 분산 기능
    - 비정상 대상을 감지하면, 해당 대상으로 트래픽 라우팅을 중단하고 대상이 다시 정상으로 감지되면 트래픽을 해당 대상으로 다시 라우팅
        
        ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2034.png)
        
- ELB 종류
    
    ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2035.png)
    
- ELB 구성(GWLB 제외)
    
    ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2036.png)
    
1. ALB(Application Load Balancer)
    - HTTP/HTTPS 요청을 로드 밸런싱 해야 하는 경우 사용
    - 웹 어플리케이션 처리에 적합
    - 리스너 규칙을 기반으로 라우팅 설정 가능함
    - 데이터 전송 보안을 위한 HTTPS 프로토콜 사용시 SSL/TLS 인증서를 배포 해야함
    - 인증서는 ACM(AWS Certificate Manager)사용 또는 클라이언트 인증서 사용 가능
    - Listener 규칙
        
        ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2037.png)
        
        - Host header : 각 요청의 호스트 이름을 기반으로 라우팅 (ex. [aaa.example.com](http://aaa.example.com) or bbb.example.com)
        - Path : 요청의 URL의 경로 패턴을 기반으로 라우팅 (ex. [www.example.com/audio](http://www.example.com/audio) or www.example.com/video)
        - Http header : 각 요청의 HTTP 헤더를 기반으로 라우팅
        - Http request method : 각 요청의 HTTP 요청 메서드를 기반으로 라우팅
        - Query string : 쿼리 문자열의 키/값 페어 또는 값을 기반으로 라우팅
        - Source IP : 각 요청의 소스 IP 주소를 기반으로 라우팅
    
    1. NLB(Network Load Balancer)
        - TCP, UDP, TSL 요청을 로드밸런싱 해야 하는 경우에 사용
        - 고도의 성능이 요구되거나 대기 시간이 낮아야 하는 애플리케이션에 적합
        - 게임 등의 수백만의 동시 사용자 처리에 적합
        - 고정 IP 주소 할당 가능
        - 클라이언트 IP 주소 전달 가능(Source IP Preservation)
        - ALB처럼 리스너 규칙 설정 없음
        - 리스너 프로토콜은 TCP,TCP/UDP,UDP,TLS를 사용할 수 있음
        - 데이터 전송 보안을 위한 HTTPS 프로토콜 사용시 SSL/TLS 인증서를 배포 해야함
        - 인증서는 ACM(AWS Certificate Manager)사용 또는 클라이언트 인증서 사용 가능
        

# EC2 Auto Scaling

- EC2 인스턴스를 자동으로 확장하고 축소하는 기능
- 사용자가 정의한 조정 정책에 따라 인스턴스 수가 증가 되거나 축소 됨
    
    ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2038.png)
    
    - ex) 서버의 로드가 증가하면 EC2 인스턴스 개수가 추가됨
    - ex) 서버의 로드가 감소하면 EC2 인스턴스 개수 줄어 듬
- EC2 Auto Scaling 구성 요소
    
    ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2039.png)
    
- EC2 Auto Scaling - 조정 정책
    - **항상 현재 인스턴스 수준 유지 관리**
        - 지정된 수의 실행 인스턴스를 항상 유지하도록 Auto Scaling 그룹을 구성
        - 인스턴스가 비정상 상태임을 확인하면 해당 인스턴스를 종료한 다음 새 인스턴스 시작
    - **수동 조정**
        - 최대, 최소 또는 원하는 욜양의 변경 사항만 지정하는 경우 사용
    - **일정을 기반으로 조정**
        - 확장 작업이 시간 및 날짜 함수에 따라 자동으로 수행됨
    - **온디맨드 기반 조정 (동적조정,Dynamic Scaling)**
        - 수요 변화에 맞춰 Auto Scaling 그룹의 크기를 동적으로 조정
        - ex) CPU 사용량을 50%기준으로 하고 사용량 기준에 따라 EC2 인스턴스 수를 증가하거나 감소
    - **예측 조정 사용(Predictive Scaling)**
        - 머신러닝을 사용하여 CloulWatch의 기록 데이터를 기반으로 용량 필요량을 예측
        

# 스토리지

데이터 저장 방식

- 오브젝트 스토리지
    - Amazon S3
    - 오브젝트라고 불리는 개별 유닛에 데이터를 저장하는 스토리지 포맷
- 블록 스토리지
    - 데이터를 고정된 사이즈의 블록으로 나누어 각각 고유한 식별자와 함께 저장하는 방식
    - Amazon EBS
        
        ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2040.png)
        
- 파일 스토리지
    - 데이터는 계층적 파일 디렉토리 내의 폴더에서 파일로 저장
    - Amazon EFS, Amazon FSx
        
        ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2041.png)
        
    
1. Elastic File System(EFS)
    - 리눅스 환경의 EC2인스턴스에 연결하기 위한 네트워크 파일 스토리지
    - Network File System(NFS)프로토콜을 지원
    - 여러 가용영역에 있는 수십~수백대의 EC2 연결 가능(고가용성, 확장성)
2. S3
    - 거의 무제한 저장용량을 제공하는 객체(Object) 스토리지 서비스
    - 최소 3개의 가용영역에 데이터를 자동 분산 저장하기에 성능, 확장성, 가용성, 내구성이 높음
    
    ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2042.png)
    
    - S3 버전관리(Versioning)
        - 객체를 하나의 파일이 아닌 여러 버전으로 보존할 수 있음
        - 실수로 객체를 덮어쓰거나 삭제한 경우 이전 버전으로 복구 가능
        - 객체(파일)이 여러 버전을 가질 수 있음
    - S3 객체 암호화
        - 서버 측 암호화(SSE- Server Side Encryption): 데이터가 서버에 저장되기 전에 객체를 암호화
            - SSE-S3: S3에서 관리하는 암호화
            - SSE-KMS: KMS(키 관리 서버)에서 관리하는 암호화
                
                키 관리 서버를 이용하므로 키를 자동 교체하거나 감사기능을 지원 가능
                
            - SSE-C: 고객(사용자)가 관리하는 암호화
            데이터 전송 시 반드시 HTTPS를 사용해야 함
        - 클라이언트 측 암호화: 데이터를 전송하기 전에 클라이언트 사이드에서 암호화
        - 전송 중 암호화: 전송 보안 프로토콜 SSL/TLS를 이용해 데이터를 암호화
        HTTPS 보안 프로토콜을 사용하여 전송
    - S3 정적 웹사이트 호스팅
        - S3에서 정적 웹사이트 호스팅 가능
        - S3에서 웹사이트 호스팅을 하면 EC2 등의 별도의 웹서버 운영을 하지 않아도 됨
        - 웹사이트 주소는 버킷이름.s3-website-리전.amazon.com형식
        - 사이트 접속시 403에러가 나오면 버킷의 퍼블릭 액세스 허용이 안되 있는 것
    - CORS(Cross-Origin Resource Sharing)
        - Origin = S3 버킷의 주소 (ex. http://website.s3-website.us-east-1.amazonaws.com
        - CORS는 다른 오리진(다른 웹주소)에 버킷에 대한 액세스를 공유하는 것
        
        ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2043.png)
        
    - 액세스 로깅(Access Logs)
        - S3 버킷의 모든 활동을 파일로 만들어 S3 버킷이 저장하는 기능
        - 감사목적으로 활용 가능
        - 로그 분석을 위해 Amazon Athena 같은 분석 도구를 사용 가능
        - 절대로 로그 파일 저장소를 같은 버킷에 하지 말 것(무한루프로 인해 로그파일 지속적 증가)
        
        ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2044.png)
        
    - S3 Replication (복제 규칙)
        - S3 버킷 간에 객체를 자동으로 복제하는 기능
            - **교차 리전 복제 (CRR, Cross Region Replication)**
                - 서로 다른 AWS 리전의 S3 버킷으로 객체를 복사
                - 사용사례: 지리적으로 가까운 액세스가 필요한 경우 재해복구(DR)
            - **동일 리전 복제 (SRR, Same Region Replication)**
                - 같은 AWS 리전의 S3 버킷으로 객체를 복사
                - 사용사례: 동일한 데이터를 사용하는 프로덕션과 테스트계정 간의 복제 법적 준수사항으로 같은 리전안에 데이터 복사본을 만들어 놓아야 하는 경우
    - S3 스토리지 클래스
        
        ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2045.png)
        
    - 객체 수명주기 관리(Lifecycle Policy)
        - 객체가 저장되어 삭제될 떄까지의 수명주기를 비용효율적으로 저장 되도록 관리하는 기능
        - 버전 관리가 활성화 되어 있을 경우 객체의 버전별로 수명 주기 정책을 적용할 수 있음
            
            ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2046.png)
            
    - S3 기타 기능
        - 이벤트 알림
            - S3의 이벤트가 발생할 때마다 알리는 기능
            - 이벤트는 객체의 생성, 복제, 복원 등이 있음
            - 생성된 이벤트 알림을 Amazon SNS, Amazon SQS, AWS Lambda로 보낼 수 있음
        - 객체 잠금
            - Object Lock, Glacier Vault lokc
    1. Storage Gateway
        - 온-프레미스 데이터 센터의 데이터와 AWS 클라우드 스토리지를 연결하는 서비스
        - 하이브리드 클라우드 스토리지로도 부름(온-프레미스 인프라 + 클라우드 인프라)
            
            ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2047.png)
            
        - 온-프레미스에 로컬캐시 기능을 통해 자주 사용되는 데이터 보관 가능
        - 온-프레미스의 데이터를 AWS클라우드로 실시간으로 전송 및 저장 가능(짧은 지연시간 액세스)
        - 파일 백업, 클라우드 파일저장소, 재해복구 저장소의 용도로 사용
        - 온-프레미스 스토리지 공간과 관련 비용 절감 효과
        1. Storage Gateway - S3 파일 게이트웨이
            - 온-프레미스와 S3간에 파일 단위로 전송하는 게이트웨이
            - NFS, SMB 프로토콜을 이용하여 S3에서 객체를 저장하고 검색 가능
            - Active Directory(AD) 서비스와 통합하여 인증된 사용자만 액세스 하도록 구성 가능
            - 온-프레미스의 파일 저장공간이 부족하여 파일을 클라우드에 저장하여 액세스 하는 경우 또는 파일을 백업용도로 클라우드에 저장하는데 사용
            
            ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2048.png)
            
        2. Storage Gateway - FSx 파일 게이트웨이
            - 온-프레미스와 Amazon FSx for Window File Server 간에 파일 단위로 전송하는 게이트웨이
            - SMB 프로토콜을 이용하여 FSx for Window File Server  내의 파일을 저장하고 검새 가능
            - Active Directory(AD) 서비스와 통합하여 인증된 사용자만 액세스 하도록 구성 가능
            - 온-프레미스의 파일 저장공간이 부족하여 파일을 클라우드에 저장하여 액세스 하는 경우 또는 파일을 백업용도로 클라우드에 저장하는데 사용
            
            ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2049.png)
            
        3. Storage Gateway - 볼륨 게이트 웨이
            - iSCSI 연결을 사용해 온-프레미스 애플리케이션에 블록 스토리지를 제공
            - 온-프레미스의 서버에서 블록 스토리지 볼륨을 iSCSI 디바이스로 연결 가능
            - 볼륨 데이터는 S3에 저장되며 볼륨을 EBS 스냅샷으로 저장 및 AWS Backup 서비스로 백업 가능
            
            ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2050.png)
            
        4. Storage Gateway - 테이프 게이트웨이
            - 온-프레미스의 테이프 백업 애플리케이션과 S3간의 전송을 위한 게이트웨이
            - 기존의 온-프레미스 테이프 백업 장치 구성을 변경하지 않아도 AWS S3로 백업 가능
        5. Storage Gateway - 하드웨어 어플라이언스
            - 스토리지 게이트웨이 운영을 위해서는 온-프레미스 서버에 Storage Gateway 애플리케이션을 설치해야 함
            - 온-프레미스에 서버등의 저장장치가 없거나 인프라가 부족한 작은 데이터 센터의 경우 Storage Gateway 소프트웨어가 미리 설치된 하드웨어 어플라이언스를 구매하여 운용 가능
                
                ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2051.png)
                
        
    2. FSx
        - FSx for Lustre
            - 리눅스 환경을 위한 고성능 병렬 스토리지 시스템
            - 병렬 스토리지 시스템 = 분산파일 시스템(Distributed File System)
            - 머신 러닝, 빅데이터 등의 고성능 컴퓨팅에 사용(HPC, HIgh Performance Computing)
            - S3 버킷과 통합 구성하여 같이 사용 가능
        - FSx for Window File Server
            - 윈도우 서버에 구축되는 파을 공유 서비스
            - Elastic File System(EFS)는 리눅스 환경의 파일 공유 서비스
            - 사용자 액세스 제어를 위해 Active Directory(AD) 서비스와 통합 가능
            - 온-프레미스 서버에서 액세스 가능
            
    3. Snow Family
        - 데이터를 네트워크가 아닌 물리적인 장치에 저장하여 전송할 수 있는 디바이스
        - 온프레미스에 있는 데이터를 AWS로 마이그레이션 해야 할 때 사용
        - 제한된 시간안에 마이그레이션, 1회성 마이그레이션, 가장 적은 시간이 소요되는 방법, 회사 네트워크 사용제한, 최저비용으로 선택간으한 옵션 등의 제약조건이 있는 경우에 선택
        - 데이터 전송절차
            - 스노우볼 디바이스 요청 > 주문자에게 디바이스 배송 > 서버에 연결하여 데이터 복사 > AWS 데이터센터로 디바이스 배송 > AWS 데이터센터에서 S3 버킷으로 데이터 복사 > 스노우볼 데이터 제거
        
        ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2052.png)
        
    4. AWS DataSync
        - 온-프레미스와 AWS간 또는 AWS 스토리지 서비스간 데이터 전송 및 복제를 자동화 하는 서비스(데이터 마이그레이션)
        - 온-프레미스 데이터를 S3, EFS, FSx for Windows File Server로 마이그레이션하거나 S3 Glacier로 아카이빙을 위해 사용
        - 전송 중 및 전송 종료 시 데이터 무결성 확인 및 암호화 가능
        - AWS 서비스 내의 스토리지 내의 데이터 이동을 위해 사용
        
        ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2053.png)
        
        - **AWS DataSync vs. AWS Snowball Edge**
            - AWS DataSync : 온라인으로 데이터 전송하는데 사용
            - Snowball Edge : 오프라인 데이터 전송, 전송대역폭이 제한, 연결이 안정적이지 못한 경우 사용
        - **AWS DataSync vs. AWS Storage Gateway**
            - AWS DataSync : 초기 데이터를 Amazon S3로 마이그레이션
            - AWS Storage Gateway : 초기 마이그레이션 이후 AWS Storage Gateway의 파일 게이트웨이 구성을 사용하여 마이그레이션된 데이터 및 온-프레미스 파일 기반 애플리케이션의 지속적인 액세스를 유지
        - **AWS DataSync vs. Amazon S3 Transfer Acceleration**
            - S3 Transfer Acceleration : S3로의 대용량 파일 전송을 위해 더 높은 처리량을 사용할 경우
        - **AWS DataSync vs. AWS Trasfer Family**
            - AWS DataSync : NFS서버, SMB파일 공유, 자제 관리형 객체 스토리지, AWS Snowcone, Amazon S3, Amazon EFS 및 Amazon FSx for Window File Server 간에 데이터 전송을 가속화 및 자동화하려는 경우
            - AWS Transfer Family : SFTP, FTPS 및 FTP 프로토콜을 사용하여 AWS S3 및 EFS와 파일 전송을 하려는 경우 사용
    5. AWS Backup
        - 중앙 집중식 백업 관리 서비스
    6. 스토리지 서비스 비교
        - S3 : 객체 스토리지, 다양한 용도에 사용하고 정적 웹사이트 호스팅에도 사용
        - S3 Glacier, S3 Glacier Deep Archive : 데이터 아카이브 용도
        - EFS : NFS 프로토콜 지원, 리눅스 네트워크 파일 시스템, 수십~수백대의 EC2 인스턴스 연결가능한 스토리지
        - FSx for Window : SMB 프로토콜 지원, 윈도우 네트워크 파일 시스템, 윈도우 파일서버 용도로 주로 사용
        - FSx for lustre : 고성능 병렬처리, 고성능 컴퓨팅HPC)를 위한 리눅스 파일 시스템
        - EBS : 1대의 EC2인스턴스만 여녈 가능한 블록 스토리지
        - Instance Store : 고성능 IOPS를 제공하는 특정 EC2에서 제공하는 블록 스토리지, 임시 저장소 용도
        - Storage Gateway : 온-프레미스와 AWS 스토리지 연결 서비스 (파일/볼륨/테이프 게이트웨이)
        - Snow Family/Snowball : 온-프레미스의 1회성 대용량 데이터 오프라인 AWS 마이그레이션을 위한 디바이스
        - DataSync : 온-프레미스 데이터를 S3, EFS, FSx for Window File Server로 온라인 마이그레이션 하는 서비스
        - AWS Backup : 중앙 집중식 백업 관리 서비스
        

# 글로벌 전송

1. CloudFront 
- 콘텐츠 전송 네트워크 서비스(CDN, Contents Delivery Network)
- 엣지 로케이션의 콘텐츠 캐싱을 이용해 콘텐츠를 사용자에게 더 빨리 배포하도록 지원하는 서비스 (엣지 로케이션은 데이터를 임시 저장 할 수 있는 캐싱 기능이 있음)
- 사용자에게 가까운 곳의 엣지로케이션에서 데이터를 전송
- 글로벌 배포
- 웹사이트 속도를 높여 해외사용자에게 향상된 브라우징 경험
- 오리진에서 CloudFront로 전송되는 비용은 부과 되지 않으므로 비용 절감 효과가 있음
- 콘텐츠 지연시간을 최소화 하면서 제공
- 비디오 콘텐츠 등 실시간 스트리밍 배포
- EC2 등 오리진 서버의 부하를 줄일 수 있음 (*오리진은 데이터 원본이 저장된 장소를 의미, S3, EC2등)
- 사용자의 요청 헤더 값(디바이스, 최종 사용자의 위치, 최종 사용자가 사용하는 언어 및 다양한 조건)에 따라 서로 다른 버전의 콘텐츠를 캐싱하여 제공할 수 있음

![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2054.png)

- CloudFront - Price Classes
    - 비용 절약을 위해 가격등급에 따라 배포되는 엣지 로케이션 수를 줄일 수 있음
    - 3가지 가격등급
        - 전체 가격 등급(Price Class All) : 모든 리전에 배포
        - 가격 등급 200(Price Class 200) : 대부분의 리전에 배포
        - 가격 등급 100(Price Class 100) : 일부 리전에 배포하며 가장 낮은 비용
        
        ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2055.png)
        
- CloudFornt - Origin Group
    - CloudFront에 대한 고가용성
    - 오리진 장애 조치를 사용하여 CloudFront를 설정
    - 기본 오리진과 보조 오리진이 포함된 오리진 그룹을 생성
    - 기본 오리진을 사용할 수 없거나 실패를 나타내는 특정 HTTP 응답 상태 코드를 반환하는 경우 CloudFront는 자동으로 보조 오리진으로 전환
    
    ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2056.png)
    
- Lambda@Edge
    - CloudFront를 통해 전달되는 콘텐츠를 사용자가 지정하는 함수를 실행할 수 있게 해주는 AWS Lambda가 확장된 컴퓨팅 서비스
- CloudFront 보안 액세스 - 뷰어 / 오리진 프로토콜 정책
    
    ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2057.png)
    
- CloudFront 보안 액세스 - OAI(Origin Access Identity)
    - OAi(Origin Access Identity)를 통해 S3버킷의 액세스를 클라우드 프론트를 통해서만 하도록 할 수 있게 하는 기능
    
    ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2058.png)
    
- CloudFront 보안 액세스
1. Global Accelerator
- 가장 가까운 위치(엣지로케이션)로 트래픽을 라우팅 하여 인터넷 대기시간을 줄이고 전송 선능을 향상하는 서비스
- 미사용 시 서버로부터 지리적으로 먼 사용자는 많은 인터넷 라우팅을 하여 속도가 느림

![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2059.png)

- 글로벌 액셀러레이터에는 2개의 Anycast 퍼블릭 고정 IP가 생성됨 (Anycast : 네트워크 트래픽을 가장 가까운 노드로 전송하는 라우팅 방식)
- Elastic IP, EC2 인스턴스, ALB, NLB 등의 AWS 엔드포인트를 연결하여 사용 가능
- 애플리케이션의 Health Check 기능을 통해 하나의 서버 장애 발생시 다른 서버로 라우팅 가능

![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2060.png)

- Global Accelerator vs. CloudFront
    - Amazon CloudFront
        - 변화하는 동적인 IP 주소 세트를 사용
        - 전세계에 분포된 엣지 로케이션을 사용
        - 엣지 로케이션을 콘텐츠를 캐시하는데 사용
        - HTTP 프로토콜을 처리하는데 적합
        - 캐시 가능한 콘텐츠(ex.이미지, 비디오)와 동적인 콘텐츠(ex.API가속화 및 동적 사이트 제공)의 성능을 개선
    - Global Accelerator
        - 고정된 IP주소를 사용
        - 전세계에 분포된 엣지 로케이션을 사용
        - 엣지 로케이션을 가장 가까운 리전의 엔드포인트로 최적화된 경로를 찾는데 사용
        - TCP, UDP프로토콜을 처리하는데 적합
        - TCP 또는 UDP를 사용하는 광범위한 애플리케이션의 성능을 개선
        - Non-HTTP를 사용하는 게임(UDP), 미디어, VolP, 모바일 앱, loT등의 다양한 애플리케이션의 성능을 향상
        - 고정 IP주소가 필요한 HTTP에 사용

# 데이터베이스

1. 관계형 데이터베이스(RDS)
    - 데이터들이 서로 연결되어 관계들로 구성된 데이터베이스
    - 데이터를 테이블 형태(스키마)로 관리하여 관계를 통해서 연결된 여러 테이블에 분산
    - 관계를 맺고 있는 데이터가 자주 변경되는 애플리케이션에서 주로 사용
    - Amazon RDS, Amazon Aurora가 대표적인 서비스
        
        ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2061.png)
        
    - RDS
        - Aurora, PostgreSQL, MySQL, MariaDB, Oracle, SQL Server등의 RDS엔진을 AWS에서는 제공
        - DB 다운타임 없이 스토리지 용량만큼 자동으로 확장 가능(Storage Auto Scaling)
        - 3가지 데이터베이스 스토리지 유형 제공
            - 범용SSD 스토리지 : 일반적인 용도
            - 프로비저닝된 IOPS SSD 스토리지 : 빠른 I/O가 필요한 경우 사용
            - 마그네틱 스토리지 : 액세스 빈도가 낮은 경우 사용
    - RDS 백업
        - 자동백업(Automated backup)
            - 백업을 수행하는 백업 기간을 설정
            - DB인스턴스를 특정 시점으로 복구 가능(Point in time recovery)
        - 데이터베이스 스냅샷(DB Snapshot)
            - 사용자가 수동으로 스냅샷 생성가능
            - 사용자가 지정한 만큼 백업을 보존할 수 있음(스냅샷 보조니간 없음)
        - 특정 시점으로 복구 또는 스냅샷에서 복구 작업을 수행하면 새로운 엔드포인트를 가지는 새 DB 인스턴스가 실행됨(필요한 경우 기존 DB 인스턴스를 삭제할 수 있음)
        - Amazon RDS DB 스냅샷과 자동 백업은 S3에 저장
    - RDS 보안
        - SSL/TLS를 사용하여 애플리케이션과 DB인스턴스 간의 전송 중 암호과 가능
        - AWS Key Management Service(KMS)를 통해 관리하는 키를 사용하여 모든 데이터베이스 엔진에 대한 저장 중 암호화ㅏ 가능
        - 암호화 되지 않는 DB인스턴스 암호화
            
            1) RDS 인스턴스 스냅샷 생성
            
            2) 암호화 된 스냅샷 복사본 생성
            
            3) 암호화 된 스냅샷에서 RDS 인스턴스 복원
            
    - RDS - 읽기 전용 복제본(Read Replica)
        - 읽기만 가능한 DB 인스턴스의 복제본을 여러개 만드는 기능
        - 읽기를 별도로 분리하여 성능을 향상
        - 원본 DB의 읽기/쓰기 트래픽을 분산시켜 성능 향상
        - SQL쿼리르 많이 하는 리포팅 툴의 경우 읽기 복제본으로 연결하여 쿼리 성능 향상
        
        ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2062.png)
        
    - RDS - 다중 AZ (Multi-AZ)
        - 데이터 베이스를 여러 가용영역애 배치 하는 것
        - 내구성과 가용성을 향상 시킬 수 있음(RDS 데이터베이스 다운타임이 가장 적게 할 수 있음)
        - 한곳의 DB가 장애 발생하면 다른 곳으로 자동연결 하도록 장애 조치 수행
        
        ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2063.png)
        
2. NoSQL 데이터베이스
    - NoSQL = non-SQL = non relational database
    - 관계구조를 갖지 않는 데이터베이스 관리 시스템
    - 대표적인 Key-Value 데이터 베이스는 Amazon DynamoDB
    
    ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2064.png)
    
    1. 인 메모리 데이터 베이스
        - 디스크가 아닌 주 메모리에 데이터를 보유하고 있는 데이터베이스
        - 데이터 양의 빠른 증가로 데이터베이스 응답 속도가 떨어지는 문제를 해결할 수 있는 대안
        - Amazon Elasticache가 대표적인 AWS 인-메모리 데이터 베이스
        
        ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2065.png)
        
        1. Neptune
            - 완전 관리형 그래프 데이터베이스 서비스
        2. 데이터 분석 서비스
            - Amazon Athena
                - 표준 SQL을 사용해 S3에 저장된 데이터를 분석할 수 있는 쿼리 서비스
            - Amazon EMR(Elastic MapReduce, MapReduce = 분산 병렬처리 컴퓨팅 모델의 이름)
                - 빅데이터 플랫폼인 Hadoop 클러스터를 손쉽게 생성해 주는 서비스
            - Amazon Redshift
                - 데이터 웨어하우스 서비스 (정보에 입각한 의사 결정을 내릴 수 있도록 분석 가능한 정보의 중앙 리포지토리)
            - AWS Glue
                - 데이터 분석을 위한 ETL(Extract, Transform and Load / 추출, 변환 및 로드) 서비스
            - AWS QuickSight
                - 클라우드 기반의 비즈니스 인텔리전스(BI) 도구
                - 대시보드, 그래프 등의 시각화를 통한 데이터 분석을 통해 의사결정을 도와주는 서비스
            - Amazon OpenSearch Service(Amazon Elastic Search Service 후속)
                - Elasticsearch에서 파생된 오픈소스, 분산 검색 및 분석 제품
                - 로그 분석, 실시간 애플리케이션 모니터링 및 웹사이트 검색 등을 쉽게 수행할 수 있게 해주는 서비스
        3. RDS On EC2
            - AWS 관리형 관계형 데이터베이스 서비스 (Relational Database Service)
            - 하드웨어 프로비저닝, 데이터베이스 설정, 패치 및 백업을 AWS에서 관리
            - SSL/TLS를 사용하여 애플리케이션과 DB 인스턴스간의 전송 중 암호화 가능
            - AWS Key Management Service(KMS)를 통해 관리하는 키를 사용하여 모든 데이터베이스 엔진에 대한 저장 중 암호화 가능
            - Aurora, PostgreSQL, MySQL, MariaDB, Oracle, SQL Server 등의 RDS 엔진을 AWS에서는 제공
        4. Aurora
            - RDS 호환형 관계형 데이터베이스
            - RDS에서 제공하는 읽기전용 복제본, KMS암호화, 스냅샷백업, 오토스케일링 등을제공
            - AWS에서 만든 서비스로 다른RDS보다 저렴한 비용에 성능이 더 뛰어남
            - 다른 RDS 보다 속도는 3-5배 빠름
            - 데이터베이스설정, 패치적용 및 백업과 같은 관리태스크를 자동화
            - Aurora DB 클러스터
                - 하나 이상의 DB 인스턴스와 이 DB 인스턴스의 데이터를 관리하는 클러스터 볼륨으로 구성
                - DB 인스턴스는 읽기/쓰기 작업을 하는 기본 DB인스턴스와 읽기 작업만 하는 Aurora 복제본으로 구성
            - Aurora 복제본(Replicas)
                - 3개의 가용영역에 6개의 데이터 사본을 자동 복제하여 고 가용성 및 성능 향상 지원
                - Aurora Auto Scaling을 사용해 워크로드에 따라 Aurora 복제본 수를 자동으로 조정 가능
            - Aurora 글로벌데이터베이스
                - 다른 리전으로 데이터베이스 복제하는 기능
                - 1초 미만의 대기 시간(PRO 1초)으로 최대 5개의 보조 리전에 복제
            - Aurora 멀티 마스터 클러스터
                - 단일 멀티 클러스터
                    - 단일 DB 인스턴스는 모든 쓰기 작업을 수행하며, 기타 모든 DB 인스턴스는 읽기 전용
                    - 라이터 DB 인스턴스가 사용 불가 상태가 되면 장애 조치 매커니즘이 읽기 전용 인스터즈 중 하나를 새 라이터로 승격
                - 멀티 마스터 클러스터
                    - 모든 DB 인스턴스는 쓰기 작업을 수행
                    - 라이터 DB 인스턴스가 사용 불가 상ㅅ태가 될 때 어떤 장애 조치도 없음
                    - 읽기/쓰기 DB 인스턴스가 사용 불가 상태가 될 때 장애 조치 프로세스 및 관련 지연이 발생하지 않음
        5. ElastiCache
            - 인메모리 데이터 스토어
            - 1밀리 초 미만의 빠른 응답시간을 제공
            - 빠른 응답이 필요한 애플리케이션에 사용 (세션 스토어, 게임 리더보드, 스트리밍 및 분석과 같이 내구성이 필요하지 않는 기본 데이터 스토어로 사용)
            - 기존의 RDS와 연결하여 DB응답성능을 개선하기 위해 사용(자주 사용하는 DB 데이터를 캐시)
            - 오픈소스 인메모리 데이터베이스 솔루션인 Redis 또는 Memcached 두가지 유형을 지원
                
                (※Memcached는 멀티쓰레드 지원, Redis는 싱글쓰레드만 지원, 일반적으로 Redis가 더 많은 기능을 지원{스냅샷 백업, 복제기능, 고가용성 제공)
                
        6. DynamoDB
            - NoSQL 데이터베이스 서비스
            - 키-값, 문서 데이터 모델 지원
            - 서버리스 서비스
            - 용량에 맞게 자동으로 확장 및 축소(Auto Scaling) 하므로 관리 및 운영 오버헤드 최소화
            - 10밀리 초 미만의 빠른 응답을 제공
            - 지연시간이 짧은, 빠른 응답이 필요한 애플리케이션에 사용 (쇼핑몰 장바구니, 은행 트랜잭션, 게임 플레이어 기록 저장 등에 사용)
            - 백업 및 복구
                - DB 테이블에 대해 온디맨드 백업을 생성하고 특정 시점으로 복구를 활성화
                - 특정 시점으로 복구 PITR(Point-in-time recovery)를 사용해 최근 35일 이내 원하는 시점으로 테이블 복원 가능
            - DynamoDB 테이블 클래스
            - 읽기/쓰기 용량 모드
            - DynamoDB Accelerator(DAX)
                - 데이터베이스 앞에 인메모리 캐시를 사용해서 DB의 성능을 향상시키는 기능 (마이크로 초 단위의 응답시간을 제공)
        7. Database Migration Service(DMS)
            - 데이터 베이스를 마이그레이션 하는 서비스 (DB -> DB)
            - 온-프레미스에서 AWS 또는 AWS내에서 마이그레이션 가능
            - 원본 DB를 사용하는 중에도 지속적으로 마이그레이션 가능
            - 같은 종류 및 서로 다른 종류 DB도 마이그레이션가능

# 애플리케이션 통합

1. Simple Queue Service(SQS)
    - Queue는 대기한다는 의미
    - SQS는 메세지를 대기하는 기능
    - 애플리케이션 간의 느슨한 결합 제공(decoupling)
    
    ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2066.png)
    
    - SQS는 Poll 방식으로 메세지를 전송 (Customer가 메세지를 요청하여 받는 방식)
    - Customer 가 메세지를 소비하면 SQS Queue에서는 메세지가 삭제됨
    
    ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2067.png)
    
    - 표준대기열 vs FIFO 대기열
    
    ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2068.png)
    
    - SQS - 배달 못한 편지 대기열(DLQ, Dead Letter Queue)
        - 일반적으로 메세지는 처리될 때까지 계속 메세지를 보냄 (이 경우, 다른 메세지처리 까지 영향을 줄 수 있음)
        - 일정 횟수 이상 시도 후 처리되지 못한 메시지는 DLQ로 이동하여 보관
        
        ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2069.png)
        
    1. Simple Notification Service(SNS)
        - 메세지 전송 서비스
        - 게시자(publisher)에서 구독자(Sbuscriber, 생산자 또는 소비자)로 메세지를 전송
        - 애플리케이션 간(A2A) 및 애플리케이션과 사용자 간(A2P) 통신
        - 전송 순서
            - SNS에서 주제(Topic) 생성 > 구독 생성(메시지를 받는 사람) > 메시지 생성 > 구독자에게 메시지 전달
        
        ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2070.png)
        
        - SNS + SQS Fan Out
            - SQS 및 SNS는 둘다 AWS 내 메시징 서비스
            - SNS를 사용하면 애플리케이션에서 정기적으로 업데이트를 확인 하거나 ‘폴링(Polling)’ 할 필요 없이 ‘푸시(Push)’ 메커니즘을 통해 다수의 구독자에게 메시지를 보낼 수 있음
            
            ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2071.png)
            
        - SNS FIFO Topic
            - SNS FIFO 주제는 메시지가 주제에 게시된 정확한 순서로 구독된 Amazon SQS FIFO 대기열에 메시지를 전달
            - SQS FIFO 대기열을 사용하면 대기열의 소비자는 메시지가 대기열로 전송된 정확한 순서로 메시지를 수신 (ex. 은행 거래 로그, 주식 시세 표시기, 항공편 추적기, 가격 업데이트, 뉴스 브로드캐스팅, 인벤토리 관리)
            
            ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2072.png)
            
        1. Kinesis
            - 실시간 스트리밍 데이터를 손쉽게 수집, 처리 및 분석 하는 서비스
            - kinesis 서비스 유형
                - Kinesis Data Streams: 데이터 스트림을 수집, 저장 및 처리
                    - 데이터 스토리지가 있음(1일~365일 사이의 기간으로 데이터 보관)
                    
                    ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2073.png)
                    
                - Kinesis Data Firehose: 데이터 스트림을 AWS 데이터 스토어에 로드
                    - 스트리밍 ETL 솔루션
                    - 거의 실시간(Near Realtime) 서비스
                    - 데이터 스토리지가 없음 (데이터를 저장하지 않음)
                    
                    ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2074.png)
                    
                - Kinesis Data Analytics: SQL 또는 Apache Flink로 데이터 스트림 분석
                    - Amazon Kinesis Data Stream 및 Amazon Kinesis Data Firehos 스트리밍 소스로부터 데이터 수집 가능
                    
                    ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2075.png)
                    
                - Kinesis Video Streams: 비디오 스트림을 수집, 저장 및 처리
        
        1. API Gateway
            - 개발자가 API를 생성, 게시, 유지관리, 모니터링 및 보안유지를 할 수 있게 하는 서비스 (API : Application Programming Interface)
            - 예) 애플리케이션 API를 통해 백엔드 시스템 및 데이터에 액세스 하여 통신
                
                ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2076.png)
                

# 보안 및 자격증명

1. AWS Cognito
    - 애플리케이션에 대한 로그인 및 인증을 제공하는 기능
    - 웹과 모바일 앱에 빠르고 사용자 가입, 로그인 및 액세스 제어 기능
    - 애플, 구글, 페이스북 등의 계정과 통합 가능
    
    ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2077.png)
    
2. AWS Single Sign On (SSO)
    - SSO는 중앙에서 관리하는 하나의 계정으로 여러 애플리케이션에 로그인하는 기능
    - AWS Organizion, Active Diretory, SAML 2.0과 통합 가능 (SAML : 인증을 지원하기 위한 표준 데이터 포맷)
    
    ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2078.png)
    
3. Key Management System (KMS)
    - 암호화 키를 생성 및 관리하는 서비스
    - KMS는 AWS에서 관리하는 소프트웨어 방식의 암호화
    - AWS에서 암호화에 관련된 서비스는 대부분 KMS와 관련됨
    - EBS, S3, RDS등의 AWS 서비스 데이터 암호화에 KMS 사용
    - 키를 자동으로 교체 하는 기능 지원
    - 감사를 위해 AWS CloudTrail과 통합되어 모든 키 사용에 관한 로그를 제공
    - 3가지 유형의 키 제공
        - **고객 관리형 키(Customer managed keys)**
            - 사용자가 생성, 소유 및 관리하는 AWS 계정의 KMS 키
            - 키 정책, IAM 정책 및 권한 부여, 암호화 구성요소 등의 제어 권한을 사용자가 가짐
        - **AWS 관리형 키(AWS managed keys)**
            - AWS 서비스가 고객의 계정에서 고객 대신 생성, 관리 및 사용하는 KMS 키
            - 키 정책, 키 삭제 등의 제어 권한이 없거나 제한이 있음
        - **AWS의 키(AWS owned keys)**
            - AWS 서비스가 여러 AWS 계정에서 사용하기 위해 소유하고 관리하는 KMS 키 모음
        
4. CloudHSM
    - CloudHSM은 AWS에서 제공하는 하드웨어 암호화 장비를 통한 하드웨어 방식의 암호화
    - KMS와 다르게 암호화 키관리는 사용자(클라이언트)가 해야함
    - 고객 제공 키(SSE-C, Customer Provided Keys)에 적합한 방식
    
    ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2079.png)
    
5. Secrets Manager
    - 보안 정보(자격증명)를 중앙 집중식으로 저장, 검색, 액세스 제어, 교체, 감사 및 모니터링 하는 서비스
    - 보안정보는 데이터베이스 자격 증명, 온-프레미스 리소스 자격 증명, SaaS 애플리케이션 자격 증명, 타사 API 키 및 Secure Shell(SSH) 키 등이 될 수 있음
    - 보안정보(자격증명, Scret)를 유지하는 방법
        - 사용자가 소유하고 AWS Key Management Service(KMS)에 저장한 암호화 키를 사용해 저장 보안 정보를 암호화
        - 사용자는 AWS Identity and Access Management(IAM) 정책을 사용하여 보안 정보에 대한 액세스를 제어
        - 사용자가 보안 정보를 검색하면 Secrets Manager가 해당 보안 정보를 복호화하여 TLS를 통해 안전하게 로컬 환경으로 전송
    - 보안정보(자격증명)을 자동으로 교체 및 관리 가능
        - Amazon RDS, Amazon Redshift 및 Amazon DocumentDB와 기본적으로 통합되며 사용자 대신 이러한 데이터베이스 자격 증명을 자동으로 교체
        - Lambda의 코드와 통합하여 30일, 60일 등의 자격증명 자동교체 날짜를 지정하여 실행가능
6. Shield
    - AWS웹 애플리케이션을 DDos(Distributed Denial of Service) 공격으로부터 보호
    - Shield Standard : 모든 사용자에게 적용(무료), SYN/UDP Flood등 기본적인 DDoS공격 보호
    - Shield는 2가지 유형을 제공
        - Shield Standard
            - 모든 AWS 사용자에게 적용되어 있음(무료)
            - SYN/UDP Flood 등 기본적인 DDoS공격 보호
        - Shiled Advanced
            - 스탠다드 서비스보다 많은 보호 제공(유료)
            - EC2, ELB, CloudFront, Route53 등에서 정교한 DDoS 보호 제공
7. WAF (Web Application Firewall)
    - 웹 애플리케이션을 보호하는 방화벽
    - HTTP (OSI 7계층)에서 동작
    - Application Load Balancer, API Gateway, CloudFornt에 적용 가능
    - WAF의 Web ACL(Access Control List)를 통해 정의할 수 있는 기능
        - 악성 IP주소 차단
        - 특정 국가의 엑세스 제어(차단)
        - SQL Injection, Cross-Site-Scripting(XSS) 방어
        - 속도기반규칙(Rate-baased rules)으로 DDoS 공격방어
8. GuardDuty, Macie, Inspector
    1. GuardDuty
        - AWS 계정 및 워크로드에서 악의적 활동을 모니터링 하고 상세한 보안 결과를 제공하는 위협 탐지 서비스
    2. Amazon Macie
        - 데이터 보안 및 데이터 프라이버시 서비스로서, 기계학습 및 패턴 일치를 활용하여 AWS에서 민감한 데이터를 검색하고 보호
    3. Amazon Inspector
        - Amazon Elastic Compute Cloud(EC2) 및 컨테이너 워크로드에서 소프트웨어 취약성과 의도하지 않는 네트워크 노출을 지속적으로 스캔하는 자동화된 취약성 관리 서비스

# 관리 및 거버넌스

1. CloudWatch
    - AWS 클라우드 리소스와 AWS에서 실행되는 애플리케이션을 위한 모니터링 서비스
    - 지표를 수집 및 추적하고 로그 파일을 수집 및 모니터링하고 경보를 설정
    - EC2 인스턴스, DynamoDB 테이블, RDS DB 인스턴스 같은 AWS 리소스뿐만 아니라 애플리케이션과 서비스에서 생성된 사용자 정의 지표 및 애플리케이션에서 생성된 모든 로그 파일을 모니터링
    - 시스템 전반의 리소스 사용률, 애플리케이션 성능, 운영 상태를 파악
    - EC2 인스턴스 DynamoDB 테이블, RDS DB 인스턴스 같은 AWS 리소스뿐만 아니라 애플리케이션과 서비스에서 생성된 사용자 정의 지표 및 애플리케이션에서 생성된 모든 로그 파일을 모니터링
    - 지표(Metrics)
        - AWS 클라우드 리소스 및 AWS에서 실행하는 애플리케이션을 모니터링
    - 대시보드(Dashboard)
        - AWS 리소스 및 사용자 정의 지표의 그래프를 한눈에 볼 수 있는 대시보드 기능
    - 로그(Logs)
        - 애플리케이션에 대한 로그를 수집하는 기능
    - 경보(Alarms)
        - 지표값에 대한 알림을 생성하는 기능
2. Amazon EventBridge
    - 거의 실시간으로 이벤트를 자동 전송 하는 서비스
    - SaaS 애플리케이션 및 AWS 서비스의 이벤트에 반응하는 애플리케이션을 구축하려고 할 때 사용
    - ex.) 이벤트 소스에 대한 EventBridge 규칙을 구성하여 Amazon SNS 주제에 메시지를 게시하여 관리자에게 이메일로 알림
    
    ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2080.png)
    

1. CloudTrail
    - AWS 계정이 수행하는 작업에 대해 로그를 기록하는 서비스
    - AWS계정의 거버넌스, 규정준수, 운영감사, 위험감사에 활용
    - 로그는 CloudWatch Log 또는 S3 버킷에 저장 가능
    - CloudTrail 로그 파일 무결성 검증 기능을 사용하여 CloudTrail에서 로그 파일을 지정된 S3 버킷으로 전송한 이후로 CloudTrail 로그 파일이 그대로 유지되거나, 삭제되거나, 수정되었는지 확인 가능
    - CloudTrail은 모든 계정에 기본으로 활성화 되어 있음
    - CloudTrail 로그 파일은 KMS 사용하여 암호화 가능
2. Config
    - AWS 리소스 구성 변경 사항을 로그기록 하는 기능
    - 버킷액세스 변경, 보안그룹 설정변경, ALB 설정 변경 등 모든 변경 사항에 대해 로그 수집 가능
    - 수집된 로그는 분석, 보안감사를 위해 S3 버킷으로 저장가능
    - 리소스 구성변경이 발생되면 알림을 SNS 주제로 전송가능
    - Config 규칙을 설정해서 AWS리소스 구성이 규정준수를 하고 있는지 평가 가능
3. AWS Organizations
    - 여러 AWS 계정을 중앙에서 관리
    - 글로벌 서비스
    - 전체 계정을 관리하는 계정을 관리계정(Master Account), 그외의 계정은 멤버 계정
    - 조직관리를 위해 OU(Organiztion Unit)이라는 조직 단위로 그룹화 하여 관리
    - 그룹마다 서비스 제어 정책(SCP, Service Control Policy)를 적용해서 액세스를 제한 해야 하는 서비스를 제어할 수 있음
    - 계정을 통합하면 결제를 한곳으로 통합 가능하고 볼륨 가격 할인을 받을 수 있음 (통합결제)
    - AWS Organiztions -OU
        - 사용중인 AWS 계정을 Root OU로 초대하여 멤버 계정으로 만들 수 있음
        
        ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2081.png)
        
    - AWS Organiztions -SCP
        - 계정에 대한 AWS 서비스 액세스 제어 정책
        - 계정에 특정 AWS 서비스에 대한 액세스를 제한할 수 있음
        - SCP 정책은 계정 또는 OU단위에 적용할 수 있음
        - OU에 적용하면 OU에 속한 계정과 OU는 모두 동일한 정책이 적용됨(정책상속)
        
        ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2082.png)
        

# 네트워크

CIDR(Classless Inter-Domain Routing)

- IP 주소 범위를 정의하는 방식
- IP 주소를 작은 그룹으로 분할 하는 것을 서브네팅이라고 함
    - ex.1) 192.168.32.1/24
        - 192.168.32.1은 기준 IP, 24는 서브넷 마스크
        - 192.168.32.1의 IP대역을 24비트로 나눈 것
        - 256개의 IP를 사용가능(192.168.32.0 ~ 192.168.32.255)
    - ex.2)
        - 192.168.32.1/16 (65534개의 IP사용가능, 192.168.0.0 ~ 192.168.255.255)
        - 192.168.32.1/25 (128개의 IP사용가능, 192.168.32.0 ~ 192.168.32.127)
        - [http://www.subnet-calculator.com/cidr.php](http://www.subnet-calculator.com/cidr.php) 에서 자동으로 계산 가능
1. VPC(Vertual Private Cloud)
    - AWS의 가상 네트워크
    - AWS서비스의 네트워크 연결을 제어하는 기능
    - AWS 계정을 생성하면 기본 VPC네트워크가 생성됨
    - 기본 VPC는 인터넷과 연결되어 있고 EC2 인스턴스를 생성하면 기본 VPC에 연결
    - VPC 구성요소
        - 서브넷 : VPC의 IP 주소 범위
        - 라우팅 테이블 : 네트워크 트래픽을 전달할 위치를 결정하는 데 사용
        - 인터넷 게이트웨이: VPC의 리소스와 인터넷 간의 통신을 연결하는 게이트웨이
        - Network ACL : 서브넷과 연결되어 서브넷의 내부와 외부의 트래픽을 제어하는 방화벽
        
        ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2083.png)
        
2. NAT Gateway
    - NAT(Network Address Translation, 네트워크 주소 변환) 서비스
    - 프라이빗 서브넷의 인스턴스가 VPC 외부의 인터넷 서비스에 연결
    
    ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2084.png)
    
    1. Security Group vs. Network Access Control List(NACL)
        - Securiy Group (보안그룹)
            - 인스턴스에 대한 인바운드 및 아웃바운드 트래픽을 제어하는 가상 방화벽 역할
            - 인스턴스 수준에서 작동
            - 보안그룹은 허용 규칙만 지정가능하고 거부 규칙은 지정할 수 없음
            - 생성된 VPC내에서만 사용 가능
        - Network Access Control List (NACL)
            - 서브넷 내부와 외부의 트래픽을 제어하는 방화벽
            - 서브넷 레벨의 연결 방화벽
            - 하나의 NACL은 여러 서브넷과 연결 가능
            - 하나의 서브넷은 하나의 NACL만 연결 가능
            - NACL은 허용, 거뷰 규칙 모두 지정 가능
            - 가장 낮은 번호가 지정된 규칙부터 시작해서 트래픽이 내부 또는 외부로 전달되도록 허용되는지 결정
            - 번호가 가장 낮은 규칙부터 평가됨
    
    ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2085.png)
    
    1. VPC Peering
        - VPC간에는 기본적으로 네트워크 통신이 되지 않음
        - VPC 피어링은 두 VPC간에 트래픽을 라우팅 할 수 있도록 하기 위한 두 VPC 사이의 네트워킹 연결
        
        ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2086.png)
        
    2. VPC Endpoint
        - S3와 DynamoDB 등 AWS 서비스에 대한 프리이빗 연결
        - 하나의 엔드포인트는 하나의 VPC에만 연결 가능
        - 엔드포인트는 동일한 리전에서만 지원, VPC와 다른 리전의 서비스 간에 엔드포인트를 생성할 수 없음
        - VPC간에 또는 서비스 간에 엔드포인트를 전송할 수 없음
        
        ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2087.png)
        
        - VPC-Endpoint - Interface Endpoints
            - 서브넷 IP 주소 범위에서 프라이빗 IP주소를 사용하는 탄력적 네트워크인터페이스
            - 지원되는 AWS 서비스 또는 VPC 엔드포인트 서비스로 전달되는 트래픽에 대한 진입점 역할
            - 엔드포인트는 동일한 리전에서만 지원, VPC와 다른 리전의 서비스 간에 엔드포인트를 생성할 수 없음
            - VPC간에 또는 서비스 간에 엔드포인트를 전송할 수 없음
        - VPC Endpoint Service (AWS PrivateLink)
            - 벤더(Service Provider)는 VPC에 애플리케이션을 구성하고 VPC Endpoint 서비스를 구성
            - 하나 또는 여러 고객(Customer) AWS 계정의 VPC Endpoint가 벤더(Provider) AWS 계정의 NLB 또는 GWLB에 연결
            - 인터넷을 통하지 않고 AWS 내부 네트워크를 통한 트래픽
            - 엔드포인트 서비스 연결시 고객과 벤더의 AWS의 리전이 같아야 함
    3. AWS PrivatLink
        - VPC와 서비스 간에 프라이빗 연결을 제공하는 기술
        - 
        
    4. VPN (Virtual Private Network)
        - 인터넷을 이용해 가상 사설망을 구성 하는 것
        - AWS Site-to-Site VPN
        - IPSec 암호화 프로토콜을 사용하여 AWS VPC와 온-프레미스간 프라이빗 네트워크를 구성
            
            
    
    ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2088.png)
    
    - AWS VPN 연결 옵션 - Client VPN
        - AWS 리소스와 클라이언트 PC와 연결하는 OpenVPN 기반의 VPN 서비스
        - Active Directory 등의 자격증명을 이용해 클라이언트가 VPN에 사용하는 권한을 부여
        - 클라이언트는 VPN접속을 위한 VPN 구성 파일이 담긴 소프트웨어를 설치
    - AWS Site-to-Site VPN(AWS Managed VPN)
        - IPSec 암호화 프로토콜을 사용 하여 AWS VPC와 온-프레미스간에 프라이빗 네트워크를 구성
        - VPC와 연결을 위한 Virtual Private Gateway 및 온-프레미스의 Customer Gateway Device의 정보를 구성하기 위한 Customer Gateway를 설정하여 VPN Tunnel 연결을 만듬
        - AWS Direct Connect의 백업으로 사용 가능
    1. Direct Connect
        - AWS와 온-프레미스 간에 DX(Direct Connect) Location을 통한 전용선을 통해 프라이빗 네트워크 연결 생성
        - VPN보다 가격이 비싸며 인터넷을 통하지 않기에 인터넷 전송 비용이 들지 않음
        - 기본적으로 암호화를 지원하지 않음(암호화를 위해 Direct Connect에 VPN을 구성 가능)
        - 트래픽이 인터넷 연결을 사용하는 Site-to-Site VPN 보다 안
        
        ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2089.png)
        
    2. Transit Gateway (TGW)
        - Transit Gateway를 통해 각 VPC 또는 VPN간의 모든 트래픽을 라우팅
        
        ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2090.png)
        
        - Transit VPC가 지원되지 않는 여러 VPC의 연결
            - 
        1. Flow Log(흐름 로그)
            - VPC의 네트워크 인터페이스에서 전송되고 수신되는 IP트래픽에 대한 정보를 수집할 수 있는 기능
            - 데이터는 아마존 CloudWatch Logs 또는 S3에 저장가능
        
        1. Route 53
            - DNS(Domain Name System) 서비스
            - DNS는 사람이 읽을 수 있는 도메인 이름(ex. www.amazon.com)을 컴퓨터가 읽을 수 있는 IP주소(ex.192.0.2.44)로 변환하는 시스템
            - Route53의 기능
                - 퍼블릭 도메인 구매 또는 이전(.com, .net, .co.kr)
                - AWS내부 VPC에서만 사용할 수 있는 프라이빗 도메인 생성
                - 라우팅 정책 적용(단순 라우팅, 가중치 기반, 지리적위치, 지연시간, 장애조치, 다중값 응답)
            
            ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2091.png)
            
            - Domain Level
            
            ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2092.png)
            
            - DNS Resolution
                
                ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2093.png)
                
                1. 사용자가 웹 브라우저에서 www.example.com을 입력
                2. www.example.com에 대한 요청이 인터넷 서비스 제공업체(IPS가 관리하는 DNS 해석기(DNS Resolver)로 라우팅
                3. ISP의 DNS 해석기는 www.example.com에 대한 요청을 DNS 루트 네임 서버에 전달
                4. ISP의 DNS 해석기는 www.[example.com](http://example.com)에 대한 욫청을 이번에는 .com 도메인의 TLD 네임 서버 중 하나에 다시 전달 .com 도메인의 네임 서버는 example.com 도메인과 연관된 Amaozn Route 53 네임 서버의 이름을 사용하여 요청에 응답
                5. ISP의 DNS 해석기는 www.example.con에 대한 요청을 Amazon Route53의 해당 네임 서버에 전달
                6.  Amazon Route53 네임 서버는 [example.com](http://example.com) 호스팅 영역에서 [www.example.com](http://www.example.com) 레코드를 찾아 웹 서버의 IP주소 192.0.2.44 등 연관된 값을 받고 이 IP 주소를 DNS 해석기로 반환  
                7. ISP의 DNS 해석기가 IP주소를 웹 브라우저로 반환합니다. 또한, DNS 해석기는 다음에 누군가가 example.com을 탐색할 때 좀 더 빠르게 응답할 수 있도록 사용자가 지정하는 일정 기간 동안 example.com의 IP 주소를 캐싱(저장)
                8. 웹 브라우저는 DNS 해석기로부터 얻은 IP 주소를 www.example.com에 대한 요청을 웹서버로 전송
                9. 192.0.2.44에 있는 웹 서버 또는 그 밖의 리소스는 www.example.com의 웹 페이지를 웹 브라우저로 반환하고, 웹 브라우저는 이 페이지를 표시
            - Route53 -TTL
                - DNS recursive resolver(ISP 업체가 운영하는 DNS 재귀적 리볼버)가 이 레코드에 관한 정보를 캐싱할 시간(초)
                
                ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2094.png)
                
            - Route53 라우팅 정책 - 장애조치(Failover)
                - 기본(Primary) 라우팅이 실패하면 보조(Secondary)로 자동 라우팅 되는 방식
                
                ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2095.png)
                
            - Route53 라우팅 정책 - 단순 라우팅(Simple)
                - 도메인 네임 → IP주소로 라우팅
                - 라우팅 대상이 여러개(ex. 2개의 IP주소)인 경우 랜덤하게 라우팅 됨
                
                ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2096.png)
                
            - Route53 라우팅 정책 - 가중치 기반(Weighted)
                - 접속자가 요청하는 횟수의 가중치(%)를 기준으로 라우팅하는 방법
                - 트래픽을 분산하거나 버전이 다른 애플리케이션을 테스트 하는 경우 유용
            - Route53 라우팅 정책 - 지연시간(Latency)
                - 지연시간(Latency)기반 라우팅은 사용자와 가까운 AWS 리전으로 라우팅
            - Route53 라우팅 정책 - 지리적 위치(Geo Location)
                - 지리적 위치 라우팅은 사용자가 속한 대륙이나 국가를 기준으로 라우팅 하는 방법
                - ex.) 한국 또는 아시아로부터 오는 트래픽을 지정된 서버 IP로 라우팅
            - Route53 라우팅 정책 - 상태 검사(Health Check)
                - 서버의 상태를 모니터링 하는 기능
                - 상태확인을 모니터링 하고 상태가 좋지 않는 경우 다른 서버로 라우팅 하는 장애조치를 구성 할 수 있음
            - Route53 라우팅 정책 - 다중값 응답(MultiValue)
                - 사용자가 요청 시 Route53 DNS에서 다수의 값을 반환하는 라우팅
                - 리소스의 상태 확인을 하여 DNS에서 상태확인에 따라 정상이 경우만 IP주소를 전달
            - 주요 DNS 레코드 유형
                - DNS 레코드를 통해 트래픽을 도메인에 라우팅 하는 방식을 DNS에 알려줌
                - A - 도메인 네임을 IPv4주소로 라우팅(www.google.com → 192.100.10.1)
                - AAAA - 도메인 네임을 IPv6 주소로 라우팅
                - CNAME - 도메인 네임을 도메인 네임으로 라우팅 (site.google.com → blog.google.com)
                - ALIAS - 도메인 네임을 AWS 리소스로 라우팅(www.google.com → AWS EC2)
                - MX(Mail eXchager) - 이메일 서버 연동시 메일의 소유를 확인하기 위한 레코드
                - NS(Name Service) - DNS레코드를 가진 DNS 서버를 식별하기 위한 레코드
                - SOA(Start of Authority) - 도메인의 정보와 권한을 가진 레코드

# 인프라 자동화

- CloudFormation
    - 코드를 통해 인프라를 프로비저닝, 관리하는 서비스가 CloudFormation
    - AWS 인프라를 프로비저닝 하는 비용과 시간을 절약 할 수 있음
    - 구성요소
        - Template : 인스턴스 유형, AMI ID, VPC, IP주소 등의 인프라를 구성하기 위한 설정 값이 있는 JSON 또는 YAML 형식의 텍스트 파일로 이루어진 템플릿
        - Stack : template을 사용하여 생성된 리소스
        - Change Set : Stack 리소스 변경 사항에 대한 세트

# 컨테이너 서비스

- 컨테이너는 애플리케이션 구성라이브러리를 패키지로 묶어서 컨테이너 엔진위에서 실행하는 것
- OS환경이 바뀌어도 구동 가능하며 각각의 컨테이너가 독립적임
- 마이크로서비스를 배포하는데 주로 사용 (마이크로서비스 : 큰 서비스를 작은 서비스의 조합으로 운영하는 것)

[https://www.notion.so](https://www.notion.so)

- Elastic Container Service(ECS)
    - Docker 컨테이너를 배포, 관리하는 컨테이너 오케스트레이션 서비스
- Amazon elastic kubernetes Service(EKS)
    - AWS에서 Kubernetes를 실행하는 서비스 (kubernetes : 대규머 컨테이너 애플리케이션을 배포, 관리하는 데 사용하는 오픈 소스 컨테이너 오케스트레이션 시스템
- AWS Fargate
    - 서버리스 컨테이너 서비스
    - 서버 프로비저닝, 패치 적용, 클러스터 용량 관리 또는 인프라 관리를 AWS에서 자동으로 수행
    - ECS 및 EKS와 연동되는 서비스
    - ECS 와 EKS 모드 Fargate를 통해 프로비저닝된 컨테이너를 사용하여 자동으로 컨테이너 크기를 조정하고 로드 밸런싱 가능
- Amazon Elastic Container Registry(Amazon ECR)
    - Docker 등의 컨테이너 이미지를 공유, 배포 등의 관리 서비스
    - ECR에서 공유된 이미지를 사용하여 ECS, EKS에서 컨테이너 구성
    

# 서버리스

- Serverless
    - 서버를 사용자가 관리할 필요가 없다는 의미
    - 실제로 서버는 존재하며, 서버 인프라 운영은 AWS등의 클라우드 회사에서 담당
    - AWS에서 용량조정, 프로비저닝, 패치 등의 인프라를 관리
    - 사용자는 필요한 애플리케이션을 구축해서 사용하기만 하면 됨
    - AWS Lambda, AWS Fargate, Amazon S3, DynomoDB, Amazon Aurora Serveless, Amazon SNS, Amazon SQS, API GateWay
- Lambda
    - 코드를 실행하여 동작하는 서버리스 컴퓨팅
    - Lambda는 AWS에서 서버 운영에 필요한 모든 인프라를 관리
    - AWS Lambda 함수는 실행당 최대 15분 동안 하도록 구성(1초에서 15분 사이의 값으로 제한 시간을 설정)
    - 동시에 처리가능한 실행 수는 1000건이며, 요청을 통해 한도 증가 가능
    - EC2는 Auto Scaling 기능을 사용해 서버를 확장하지만, Lambda는 사용량이 늘어나면 자동으로 용량이 확장되므로 용량 계획이 필요 없고 확장성이 뛰어남
    - Lambda는 독립적으로 사용하지 않고 다른 서비스와 결합하여 사용됨 (API GateWay, Kinesis, DynamoDB, SNS, SQS, S3, CloudFront
        
        ![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2097.png)
        
    

# Elastic Beanstalk

- 웹 애플리케이션 및 서비스를 배포하고 운영하는 서비스
- 사용자가 직접 인프라 리소스를 구성할 필요 없고, 애플리케이션 코드에만 집중하면 됨
- 코드를 업로드하기만 하면 Elastic Beanstalk가 용량 프로비저닝, 로드 밸런싱, Auto Scaling부터 시작하여 애플리케이션 상태 모니터링 등의 배포를 AWS에서 자동으로 처리

![Untitled](AWS%20Certified%20Solutions%20Architect%20-%20Associate%20f554eea75b344ee0b8ad143a771ffb01/Untitled%2098.png)