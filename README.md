# AWS CPP

# 클라우드 컴퓨팅의 이점

**보안(Security)** 

- 광범위한 보안 정책 집합, 기술 및 컨트롤을 제공하여 데이터, 앱 및 인프라를 잠재적인 위협으로부터 보호

**안정성(Reliability)** 

- 클라우드 공급자 네트워크의 여러 중복 사이트에 데이터를 미러할 수 있으므로 데이터 백업, 재해 복구 및 비즈니스 연속성을 더 쉽게 제공

**고가용성(High Availability)** 

- 클라우드 공급자의 여러 리전, 가용영역, 데이터센터를 활용하여 고가용성을 쉽게 설계 가능
- 고가용성 설계를 통해 다운 타임을 최소화 하면서 장애를 견딜 수 있는 아키텍처 설계 가능
- 예를 들어 여러 가용영역(여러 데이터센터)에 Amazon EC2 인스턴스를 배치

**탄력성(Elasticity), 확장성(Scalability)**

- 더 이상 어떤 용량이 필요할지 추측할 필요가 없으며 사용자는 리소스 용량에 대한 추측을 중지 가능
- 사용자는 필요에 따라 컴퓨팅 용량을 프로비저닝 하거나 해제 가능 하며 현재 수요를 처리하는 데 필요한 양의 리소스 만 프로비저닝 가능
- 수요 변화에 따라 리소스 크기를 조정 가능
- 매우 동적인 사용 패턴(워크로드)을 지원하기 위해 알림 기능으로 자동 확장 및 축소 가능

 **민첩성(Agility)** 

- 프로비저닝 시간이 짧은 즉시 사용 가능한 리소스, 확장 가능한 컴퓨팅 용량 제공
- 새로운 워크로드를 배포하는 데 필요한 직원의 시간 단축 하여 애플리케이션 개발 팀의 생산성 향상 • 개발자가 IT 리소스를 사용할 수 있도록 하는 데 필요한 시간 단축을 통해 혁신을 지원하는 능력 제공
- 새로운 기능을 반복적인 방식으로 신속하게 제공하여 출시 시간을 최소화
- 예를 들어 스타트 업이 빠르게 시장에 출시해야하는 새로운 애플리케이션을 개발 하여 빠르게 클라우드에 배포 및 필요할 때마다 빠르게 조정 가능

 **사용한 만큼 지불하는 요금제 (Pay-as-you go pricing)** 

- 장기 계약이 필요하지 않은 종량제 모델을 사용
- 초기 고정 비용/자본 비용(CAPEX)를 변동 비용/가변 비용(OPEX)으로 대체할 수 있도록 하는 온디맨드 기술 서비스 사용
- 큰 자본 지출을 최소화함으로써 총 소유 비용 (TCO)을 어떻게 줄일 수 있음

**글로벌 도달 (Global Reach, Global Footprint)** 

- 지연 시간이 짧은 높은 처리량과 중복성을 가진 네트워크로 연결된 여러 지역으로 구성된 클라우드 인프라를 배포
- 회사의 서비스를 빠르게 글로벌화할 수 있는 능력 • AWS 리전, 가용 영역 및 엣지 로케이션 네트워크를 통해 전 세계 사용자에게 애플리케이션을 배포
- 데이터를 기본 사용자와 가깝게 저장 가능

**규모의 경제 (Economy of scale)** 

- AWS등의 클라우드 회사에서 높은 구매량으로 인해 변동 비용을 낮출 수 있음
- AWS 클라우드 요금의 지속적인 감소 • 온-프레미스 데이터 센터를 구축하고 유지 관리하는 데 드는 많은 비용을 없애 줌

**기타 클라우드 컴퓨팅 이점** 

- 클라우드 업체에서 인프라를 관리하기에 사용자는 데이터 센터 유지 관리에 돈을 쓰지 않아도 됨
- 데이터센터 인프라는 클라우드 업체에서 관리하기에 사용자는 수익 창출(비즈니스) 활동에 집중할 수 있음
- AWS 관리형 서비스를 활용하면 사용자 관리가 최소화 되므로 AWS 클라우드에서 운영 효율성을 높일 수 있음
- 반복되는 애플리케이션 설치 및 설정을 돕기 위해 클라우드 업체의 엔터프라이즈 지원을 사용하여 효율을 높일 수 있음

# AWS 글로벌 인프라

1. 리전(Region)
    - 데이터 센터를 클러스터링 하는 물리적 위치
    - 1개 AWS리전 = 2개이상의 가용영역으로 구성
2. 가용영역
    - 가용영역 = 하나 이상의 개별 데이터 센터
    - 1개의 리전은 2개이상의 가용영역으로 구성 (보통 3~4개의 가용영역으로 구성)
    - 고가용성 설계 = 다중(Multi-AZ), 2개 이상의 가용영역에 시스템 배치
3. 엣지 로케이션(Edge Location)
    - 엣지 로케이션에 콘텐츠(데이터)를 캐싱하여 사용자에게 더 짧은 지연시간으로 콘텐츠 전송
    - 글로벌 배포 서비스인 AWS CloudFront, Global Accelerator에서 대표적으로 사용
    - 엣지로케이션과 AWS 리전, 가용영역끼리는 고속 네트워크로 연결되어 있음

![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled.png)

# 클라우드 컴퓨팅 모델 - 공급자와 사용자 관리

![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%201.png)

**IaaS – Infrastructure as a service**

- 물리적인 부분은 공급자가 관리
- 사용자는 운영체제, 스토리지, 애플리케이션 관리
- Amazon EC2 가 대표적인 서비스

**PaaS – Platform as a service**

- 물리적인 부분, OS 등 공급자가 모든 플랫폼 관리
- 사용자는 데이터와 애플리케이션만 관리
- 사용자는 애플리케이션 개발에만 집중 가능
- AWS Elastic Beanstalk 이 대표적인 서비스

**SaaS – Software as a service**

- 모든 부분을 공급자가 관리
- 사용자는 서비스를 사용만 하면 됨
- Google Gmail 등이 대표적인 서비스

# **AWS 인터페이스**

![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%202.png)

# **AWS Identity and Access Management (IAM)**

**IAM 개요**

- AWS 계정 및 권한 관리 서비스
- AWS 서비스와 리소스에 대한 액세스 관리
- 사용자, 그룹, 역할, 정책으로 구성
- 리전에 속하는 서비스가 아닌 글로벌 서비스
- 계정 보안 강화를 위해
✓ 루트 계정(AWS회원가입시 만들어지는 계정)은 최초 사용자 계정 생성 이후 가능하면 사용하지 말 것
✓ 사용자 계정(IAM 계정)으로 서비스를 사용하고 사용자는 필요한 최소한의 권한만 부여(최소권한의 원칙)
✓ 루트계정과 개별 사용자 계정에 강력한 암호 정책과 멀티팩터 인증(MFA) 적용
✓ 사용자의 암호에 대한 복잡성 요구 사항과 의무 교체 주기를 정의
✓ 액세스 키(Access Key)는 공유하지 말 것

**IAM 루트 사용자 자격 증명을 요구하는 작업**

- 계정 설정을 변경(계정 이름, 이메일 주소, 루트 사용자 암호 및 루트 사용자 액세스 키). 연락처 정보, 결제 통화 기본 설
정 및 리전과 같은 기타 계정 설정에는 루트 사용자 자격 증명이 필요하지 않음
- IAM 사용자 권한을 복원. IAM 관리자가 실수로 권한을 취소하면 루트 사용자로 로그인하여 정책을 편집하고 해당 권한
을 복원
- Billing and Cost Management 콘솔에 대한 IAM 액세스 활성화
- 특정 세금 계산서를 조회
- AWS 계정을 닫음
- AWS 지원 플랜(Support Plan)을 변경하거나 AWS 지원 플랜을 취소
- 예약 인스턴스 마켓플레이스에 판매자로 등록
- MFA (멀티 팩터 인증) Delete를 활성화하도록 Amazon S3 버킷을 구성
- 잘못된 VPC ID 또는 VPC 엔드포인트 ID가 들어 있는 Amazon S3 버킷 정책을 편집하거나 삭제
- GovCloud 등

**IAM - 정책**

- AWS 리소스에 대한 액세스 권한을 정의 한 것
- 사용자, 그룹, 역할에 정책을 연결하여 사용
- 가능하면 정책을 개별 사용자에게 직접 부여하지 말고 사용자가 속한 그룹에 권한 부여
- IAM 정책 종류
✓ AWS 관리형 정책 : AWS에서 생성 및 관리하는 정책
✓ 고객 관리형 정책(사용자 지정 정책) : 사용자가 직접 생성 및 관리하는 정책
✓ 인라인 정책 : 사용자, 그룹, 역할에 직접 생성하는 정책
✓ 대부분의 경우 관리형 정책을 사용하는 것을 권장

**IAM - 역할**

- AWS 리소스에서 사용하는 자격증명
- 특정 AWS 서비스가 다른 AWS 서비스에 액세스 하여 작업을 수행할 때 필요한 권한
- 정책을 연결하여 IAM 역할에 작업 수행에 필요한 권한을 부여
- 만일, EC2에서 실행되는 애플리케이션이 AWS S3와 AWS RDS 액세스 권한이 필요할 때 역할 사용

![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%203.png)

**IAM 자격증명 보고서 (Credentials Report)**

- 계정의 모든 사용자와 암호, 액세스 키, MFA 디바이스 등 이들의 자격 증명 상태를 나열하는 자격 증명 보
고서를 생성하고 다운로드
- 보고서 내용
✓ 사용자의 표시 이름
✓ 사용자의 Amazon 리소스 이름(ARN)
✓ 사용자가 생성된 날짜 및 시간
✓ 사용자의 암호가 마지막으로 사용된 날짜 및 시간
✓ 계정에 암호 교체를 요구하는 암호 정책이 있는 경우, 사용자가 새 암호를 설정해야 할 때 이 필드에 날짜 및 시간
✓ 사용자에 대해 멀티 팩터 인증(MFA) 디바이스를 사용하도록 설정되었는지 여부
✓ 사용자에게 액세스 키가 있고 액세스 키의 상태가 활성인지 여부
✓ 사용자의 액세스 키가 생성되었거나 마지막으로 변경된 날짜 및 시간
✓ 사용자의 액세스 키를 AWS API 요청 서명에 마지막으로 사용한 날짜 및 시간
✓ 액세스 키가 마지막으로 사용된 AWS 리전
✓ 액세스 키로 가장 최근에 액세스한 AWS 제품

# 시스템 아키텍처

- 확장성 (Scalability)
    
    ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%204.png)
    
- 고 가용성 (High Availability)
    - AWS에서는 여려 가용영역(서로 다른 데이터센터)에 시스템을 분산 배치하는 방법을 고가용성 설계라고 함
    - 장애를 대비하여 시스템을 이중화 하는 것
    
    ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%205.png)
    
- 느슨한 결합(Loosely Coupled)
    - 한 시스템의 상태가 다른 쪽에 영향을 덜 미치는 결합
    
    ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%206.png)
    
- Load Balancer
    - 트래픽을 분산하는 서비스 (여러 리전에 배포 불가)
    - 비정상 대상을 감지하면, 해당 대상으로 트래픽 라우팅을 중단하고 대상이 다시 정상으로 감지되면 트래픽을 해당 대상으로 다시 라우팅
        
        ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%207.png)
        
    - Elastic Load Balancer 종류
        
        ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%208.png)
        
- EC2 Auto Scaling
    - EC2 인스턴스를 자동으로 확장하고 축소하는 기능
    
    ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%209.png)
    
    - EC2 Auto Scaling 구성요소
        
        ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%2010.png)
        
    - EC2 Auto Scaling - 조정정책
        - **항상 현재 인스턴스 수준 유지 관리**
            - 인스턴스가 비정상 상태임을 확인하면 해당 인스턴스를 종료한 다음 새 인스턴스를 시작
            - 지정된 수의 실행 인스턴스를 항상 유지하도록 Auto Scaling 그룹을 구성
        - **수동 조정**
            - 최대, 최소 또는 원하는 용량의 변경 사항만 지정하는 경우 사용
        - **일정을 기반으로 조정**
            - 확장 작업이 시간 및 날짜 함수에 따라 자동으로 수행됨 • 예, 매주 일요일에는 인스턴스 4대, 다른 요일에는 2대 실행
        - **온디맨드 기반 조정**
            - 수요 변화에 맞춰 Auto Scaling 그룹의 크기를 동적으로 조정
            - 예, CPU 사용량을 50%기준으로 하고 사용량 기준에 따라 EC2 인스턴스 수를 증가하거나 감소
        - **예측 조정 사용 (Predictive Scaling)**
            - 머신러닝을 사용하여 CloudWatch의 기록 데이터를 기반으로 용량 필요량을 예측
    - EC2 Auto Scaling - 동적 조정(Dynamic Scaling)
        - **대상 추적 조정(Target Tracking Scaling)**
            - ****지정한 지표가 목표값을 초과할 때 한해서 Auto Scaling 그룹을 확장 하는 방식
            - 예, CPU 사용률 목표값을 50%로 설정한 후 Auto Scaling 그룹이 목표값을 초과하면 EC2 인스턴스 증가 • CPU 평균 사용률, 네트워크 인터페이스에서 송/수신한 평균 바이트 수, 로드발란서 요청 수 등의 지표 사용 가능
        - **단계 조정(Step Scaling)** • CloudWatch alarm의 지표를 기반으로 Auto Scaling 그룹을 확장 하는 방식
            - 예, CPU 사용률이 60% 초과하면 Auto Scaling Group 10% 증가 CPU 사용률이 30% 이하면 Auto Scaling Group 10% 감소
        - **단순 조정(Simple Scaling)** • CloudWatch alarm의 지표를 기반으로 Auto Scaling 그룹을 확장 하는 방식
            - 예, CPU 사용률이 60% 초과하면 EC2 인스턴스 2개 증가 CPU 사용률이 30% 이하면 EC2 인스턴스 1개 감소
        

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
    - 전용 호스트/전용 인스턴스 → 전용 물리적 서버를 할당 받아서 인스턴스를 사용
- Elastic Network Interface(ENI)
    - 가상 네트워크 인터페이스
    - 인스턴스에 연결되어 네트워크 통신을 하는 역할
    
    ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%2011.png)
    
- 보안그룹
    - EC2 인스턴스에 대한 인바운드 및 아웃바운드 트래픽을 제어하는 인스턴스 수준의 방화벽
    - 보안그룹은 허용규칙만 지정 가능하고 거부 규칙은 지정할 수 었음
    
    ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%2012.png)
    
- EC2 스토리지
    1. Elastic Block Store(EBS)
        - EC2에 연결하여 사용하는 블록 스토리지
        - 여러 개의 EBS 볼륨을 생성하여 EC2에 추가 연결 가능
    2. Amazon Machine Image(AMI)
        - OS, 애플리케이션, 서버 프로그램 설정 등이 미리 구성된 이미지
        - EC2 인스턴스를 시작하는데 AMI 사용하여 EC2 시작 시 OS 설치나 서버 소프트웨어 설정 등을 별도로 할 필요 없음
    3. EC2 Image Builder
        - Amazon EC2 및 온프레미스에서 사용할 Linux 또는 Window 이미지의 생성, 유지 관리, 검증, 공유 및 배포를 간소화 하는 서비스
        
        ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%2013.png)
        
    4. Instance Store
        - 블록 수준의 임시 스토리지
        - 임시 파일을 보관하는 가장 빠른 성능의 저장 옵션
        - EC2 인스턴스가 종료되면 데이터가 삭제 되므로 영구적인 저장소가 아닌 고성능을 요구하는 애플리케이션의 임시저장소로 적합
    5. Elastic File System(EFS)
        - 리눅스 환경의 EC2 인스턴스에서 연결하기 위한 네트워크 파일 스토리지
        - Network File System(NFS) 프로토콜을 지원
        
        ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%2014.png)
        
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
                

# 컴퓨팅 - 기타

Serverless

- 서버를 사용자가 관리할 필요가 없다는 의미
- 서버는 실제로 존재하며 서버 인프라 운영은 AWS등 클라우드 회사에서 담당
- AWS에서 용량조정, 프로비저닝, 패치 등의 인프라를 관리
- 대표적인 AWS 서버리스 서비스
    
    AWS Lambda, AWS Fargate, Amazon S3, DynomoDB, Amazon Aurora Serveless, Amazon SNS, Amazon SQS, API GateWay
    

1. Lambda
    - 코드를 실행하여 동작하는 서버리스 컴퓨팅
    - EC2는 Auto Scaling 기능을 사용해 서버를 확장하지만, Lambda는 사용량이 늘어나면 자동으로 용량이 확장되므로 용량 계획이 필요 없고 확장성이 뛰어남
    - Lambda는 독립적으로 사용하지 않고 다른 서비스와 결합하여 사용됨 (API GateWay, Kinesis, DynamoDB, SNS, SQS, S3, CloudFront
        
        ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%2015.png)
        
    
2. AWS Batch
    - AWS에서 배치 컴퓨팅 작업을 효율적으로 손쉽게 실행할 수 있게 해주는 서비스
    - 자동으로 컴퓨팅 리소스를 프로비저닝 하고 워크로드 양 및 규모에 따라 워크로드 분배를 최적화
    - 배치 작업은 Docker 컨테이너 이미지로 정의 되어 Elastic Container Services(ECS)에서 실행됨
3. Container
    - 컨테이너는 애플리케이션 구성라이브러리를 패키지로 묶어서 컨테이너 엔진 위에서 실행하는 것
    
    ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%2016.png)
    
    - 마이크로서비스를 배포하는데 주로 이용
    - AWS 컨테이너 서비스
        - Elastic Container Service(ECS)
            - Docker 컨테이너를 배포, 관리하는 컨테이너 오케스트레이션 서비스
        - Amazon Elastic Kubernetes Service(EKS)
            - Kubernetes는 대규모 컨테이너 애플리케이션을 배포, 관리하는 데 사용하는 오픈 소스 컨테이너 오케스트레이션 시스템
        - AWS Fargate
            - 서버리스 컨테이너 서비스
            - 서버 프로비저닝, 패치 적용, 클러스터 용량 관리 또는 인프라 관리를 AWS에서 자동으로 수행
            - Amazon Elastic Container Service(ECS) 및 Amazon Elastic Kubernetes Service(EKS)와 연동되는 서비스
            - ECS와 EKS 모두 Fargate를 통해 프로비저닝된 컨테이너를 사용하여 자동으로 컨테이너 크기를 조정하고 로드 밸런
            싱 가능
        - Amazon Elastic Container Registry(Amazon ECR)
            - Docker 등의 컨테이너 이미지를 공유, 배포 등의 관리 서비스
            - ECR에서 공유된 이미지를 사용하여 ECS, EKS에서 컨테이너 구성
4. Lightsail
    - 웹 애플리케이션 또는 웹 사이트를 클릭 몇 번으로 설정하고 실행할  수 있는 사용이 쉬운 클라우드 리소스
    - 클라우드 경험이 없는 사용자를 위한 서비스
    - 서비스를 저렴하고 예측 가능한 월간 요금으로 사용가능
5. Amazon WorkSpaces
    - 클라우드 기반 윈도우 또는 리눅스 데스크톱 가상화 서비스
6. Amazon AppStream 2.0
    - 애플리케이션 및 데스크톱 스트리밍 서비스
7. Elastic Beanstalk
    - 웹 애플리케이션 및 서비스를 배포하고 운영하는 서비스
    - 코드를 업로드하기만 하면 Elastic Beanstalk가 용량 프로비저닝, 로드 밸런싱, Auto Scaliing 부터 시작하여 애플리케이션 상태 모니터링 등의 배포를 AWS에서 자동으로 처리

# 스토리지

데이터 저장 방식

- 오브젝트 스토리지
    - Amazon S3
    - 오브젝트라고 불리는 개별 유닛에 데이터를 저장하는 스토리지 포맷
- 블록 스토리지
    - 데이터를 고정된 사이즈의 블록으로 나누어 각각 고유한 식별자와 함께 저장하는 방식
    - Amazon EBS
- 파일 스토리지
    - 데이터는 계층적 파일 디렉토리 내의 폴더에서 파일로 저장
    - Amazon EFS, Amazon FSx
    

1. S3
    - 거의 무제한 저장용량을 제공하는 객체(Object) 스토리지 서비스
    - 최소 3개의 가용영역에 데이터를 자동 분산 저장하기에 성능, 확장성, 가용성, 내구성이 높음
    
    ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%2017.png)
    
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
    - 액세스 로깅(Access Logs)
        - S3 버킷의 모든 활동을 파일로 만들어 S3 버킷이 저장하는 기능
        - 감사목적으로 활용 가능
        - 로그 분석을 위해 Amazon Athena 같은 분석 도구를 사용 가능
    - S3 Replication (복제 규칙)
    - S3 버킷 간에 객체를 자동으로 복제하는 기능
        - **교차 리전 복제 (CRR, Cross Region Replication)**
            - 서로 다른 AWS 리전의 S3 버킷으로 객체를 복사
            - 사용사례: 지리적으로 가까운 액세스가 필요한 경우 재해복구(DR)
        - **동일 리전 복제 (SRR, Same Region Replication)**
            - 같은 AWS 리전의 S3 버킷으로 객체를 복사
            - 사용사례: 동일한 데이터를 사용하는 프로덕션과 테스트계정 간의 복제 법적 준수사항으로 같은 리전안에 데이터 복사본을 만들어 놓아야 하는 경우
    - S3 스토리지 클래스
        
        ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%2018.png)
        
    
    1. Storage Gateway
        - 온-프레미스 데이터 센터의 데이터와 AWS 클라우드 스토리지를 연결하는 서비스
            
            ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%2019.png)
            
        - 온-프레미스에 로컬캐시 기능을 통해 자주 사용되는 데이터 보관 가능
    2. FSx
        - FSx for Lustre
            - 리눅스 환경을 위한 고성능 병렬 스토리지 시스템
            - 병렬 스토리지 시스템 = 분산파일 시스템(Distributed File System)
        - FSx for Window File Server
            - 윈도우 서버에 구축되는 파을 공유 서비스
            - Elastic File System(EFS)는 리눅스 환경의 파일 공유 서비스
            
    3. Snow Family
        - 데이터를 네트워크가 아닌 물리적인 장치에 저장하여 전송할 수 있는 디바이스
        - 온프레미스에 있는 데이터를 AWS로 마이그레이션 해야 할 때 사용
        
        ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%2020.png)
        
    4. AWS DataSync
        - 온-프레미스와 AWS간 또는 AWS 스토리지 서비스간 데이터 전송 및 복제를 자동화 하는 서비스(데이터 마이그레이션)
        - 온-프레미스 데이터를 S3, EFS, FSx for Windows File Server로 마이그레이션하거나 S3 Glacier로 아카이빙을 위해 사용
        
        ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%2021.png)
        
        - **AWS DataSync vs. AWS Snowball Edge**
            
            • AWS DataSync : 온라인으로 데이터 전송하는데 사용
            
            • Snowball Edge : 오프라인 데이터 전송, 전송대역폭이 제한, 연결이 안정적이지 못한 경우 사용 
            
        - **AWS DataSync vs. AWS Storage Gateway**
            
            • AWS DataSync : 초기 데이터를 Amazon S3로 마이그레이션 
            
            • AWS Storage Gateway : 초기 마이그레이션 이후 AWS Storage Gateway의 파일 게이트웨이 구성을 사용하여 마이그레 이션된 데이터 및 온-프레미스 파일 기반 애플리케이션의 지속적인 액세스를 유지
            
    5. AWS Backup
        - 중앙 집중식 백업 관리 서비스

# 데이터베이스

1. 관계형 데이터베이스(RDS)
    - 데이터들이 서로 연결되어 관계들로 구성된 데이터베이스
    - 데이터를 테이블 형태(스키마)로 관리하여 관계를 통해서 연결된 여러 테이블에 분산
    - 관계를 맺고 있는 데이터가 자주 변경되는 애플리케이션에서 주로 사용
    - Amazon RDS, Amazon Aurora가 대표적인 서비스
2. NoSQL 데이터베이스
    - NoSQL = non-SQL = non relational database
    - 관계구조를 갖지 않는 데이터베이스 관리 시스템
    - 대표적인 Key-Value 데이터 베이스는 Amazon DynamoDB
    
    ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%2022.png)
    
    1. 인 메모리 데이터 베이스
        - 디스크가 아닌 주 메모리에 데이터를 보유하고 있는 데이터베이스
        - 데이터 양의 빠른 증가로 데이터베이스 응답 속도가 떨어지는 문제를 해결할 수 있는 대안
        - Amazon Elasticache가 대표적인 AWS 인-메모리 데이터 베이스
        
        ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%2023.png)
        
        1. Neptune
            - 완전 관리형 그래프 데이터베이스 서비스
        
        1. 데이터 분석 서비스
            - Amazon Athena
                - 표준 SQL을 사용해 S3에 저장된 데이터를 분석할 수 있는 쿼리 서비스
            - Amazon EMR(Elastic MapReduce)
                - 빅데이터 플랫폼인 Hadoop 클러스터를 손쉽게 생성해 주는 서비스
            - Amazon Redshift
                - 데이터 웨어하우스 서비스 (정보에 입각한 의사 결정을 내릴 수 있도록 분석 가능한 정보의 중앙 리포지토리)
            - AWS Glue
                - 데이터 분석을 위한 ETL(Extract, Transform and Load / 추출, 변환 및 로드) 서비스
            - AWS QuickSight
                - 클라우드 기반의 비즈니스 인텔리전스(BI) 도구
                - 대시보드, 그래프 등의 시각화를 통한 데이터 분석을 통해 의사결정을 도와주는 서비스
        2. RDS On EC2
            - AWS 관리형 관계형 데이터베이스 서비스 (Relational Database Service)
            - 하드웨어 프로비저닝, 데이터베이스 설정, 패치 및 백업을 AWS에서 관리
            - SSL/TLS를 사용하여 애플리케이션과 DB 인스턴스간의 전송 중 암호화 가능
            - AWS Key Management Service(KMS)를 통해 관리하는 키를 사용하여 모든 데이터베이스 엔진에 대한 저장 중 암호화 가능
            - Aurora, PostgreSQL, MySQL, MariaDB, Oracle, SQL Server 등의 RDS 엔진을 AWS에서는 제공
        3. Aurora
            - RDS 호환형 관계형 데이터베이스
            - RDS에서 제공하는 읽기전용 복제본, KMS암호화, 스냅샷백업, 오토스케일링 등을제공
            - AWS에서 만든 서비스로 다른RDS보다 저렴한 비용에 성능이 더 뛰어남
            - 다른 RDS 보다 속도는 3-5배 빠름
            - 데이터베이스설정, 패치적용 및 백업과 같은 관리태스크를 자동화
        4. ElastiCache
            - 인메모리 데이터 스토어
            - 1밀리 초 미만의 빠른 응답시간을 제공
            - 빠른 응답이 필요한 애플리케이션에 사용
            - 기존의 RDS와 연결하여 DB응답성능을 개선하기 위해 사용
        5. DynamoDB
            - NoSQL 데이터베이스 서비스
            - 키-값, 문서 데이터 모델 지원
            - 서버리스 서비스
            - 용량에 맞게 자동으로 확장 및 축소(Auto Scaling) 하므로 관리 및 운영 오버헤드 최소화
        6. Database Migration Service(DMS)
            - 데이터 베이스를 마이그레이션 하는 서비스 (DB -> DB)
            - 온-프레미스에서 AWS 또는 AWS내에서 마이그레이션 가능
            - 원본 DB를 사용하는 중에도 지속적으로 마이그레이션 가능
            - 같은 종류 및 서로 다른 종류 DB도 마이그레이션가능

# 네트워크

1. VPC(Vertual Private Cloud)
    - AWS의 가상 네트워크
    - AWS서비스의 네트워크 연결을 제어하는 기능
    - VPC 구성요소
        - 서브넷 : VPC의 IP 주소 범위
        - 라우팅 테이블 : 네트워크 트래픽을 전달할 위치를 결정하는 데 사용
        - 인터넷 게이트웨이: VPC의 리소스와 인터넷 간의 통신을 연결하는 게이트웨이
        - Network ACL : 서브넷과 연결되어 서브넷의 내부와 외부의 트래픽을 제어하는 방화벽
        
        ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%2024.png)
        
2. NAT Gateway
    - NAT(Network Address Translation, 네트워크 주소 변환) 서비스
    - 프라이빗 서브넷의 인스턴스가 VPC 외부의 인터넷 서비스에 연결
    
    ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%2025.png)
    
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
    
    ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%2026.png)
    
    1. VPC Peering
        - VPC간에는 기본적으로 네트워크 통신이 되지 않음
        - VPC 피어링은 두 VPC간에 트래픽을 라우팅 할 수 있도록 하기 위한 두 VPC 사이의 네트워킹 연결
        
        ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%2027.png)
        
    2. VPC Endpoint
        - S3와 DynamoDB 등 AWS 서비스에 대한 프리이빗 연결
        
        ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%2028.png)
        
    3. VPN (Virtual Private Network)
        - 인터넷을 이용해 가상 사설망을 구성 하는 것
        - AWS Site-to-Site VPN
            - IPSec 암호화 프로토콜을 사용하여 AWS VPC와 온-프레미스간 프라이빗 네트워크를 구성
            
    
    ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%2029.png)
    
    1. Direct Connect
        - AWS와 온-프레미스 간에 DX(Direct Connect) Location을 통한 전용선을 통해 프라이빗 네트워크 연결 생성
        - VPN보다 가격이 비싸며 인터넷을 통하지 않기에 인터넷 전송 비용이 들지 않음
        
        ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%2030.png)
        
    2. Transit Gateway (TGW)
        - Transit Gateway를 통해 각 VPC 또는 VPN간의 모든 트래픽을 라우팅
        
        ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%2031.png)
        
        1. Flow Log(흐름 로그)
            - VPC의 네트워크 인터페이스에서 전송되고 수신되는 IP트래픽에 대한 정보를 수집할 수 있는 기능
            - 데이터는 아마존 CloudWatch Logs 또는 S3에 저장가능
        
        1. Route 53
            - DNS(Domain Name System) 서비스
            - DNS는 도메인 네임을 IP주소로 변환해주는 기능
            
            ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%2032.png)
            
            - Route53 라우팅 정책 - 장애조치(Failover)
                - 기본(Primary) 라우팅이 실패하면 보조(Secondary)로 자동 라우팅 되는 방식
                
                ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%2033.png)
                

# 글로벌 전송

1. CloudFront
    - 콘텐츠 전송 네트워크 서비스(CDN, Contents Delivery Network)
    - 엣지 로케이션의 콘텐츠 캐싱을 이용해 콘텐츠를 사용자에게 더 빨리 배포하도록 지원하는 서비스 (엣지 로케이션은 데이터를 임시 저장 할 수 있는 캐싱 기능이 있음)
    - 콘텐츠 지연시간을 최소화 하면서 제공
    - 비디오 콘텐츠 등 실시간 스트리밍 배포
    - EC2 등 오리진 서버의 부하를 줄일 수 있음
2. Global Accelerator
    - 가장 가까운 위치(엣지로케이션)로 트래픽을 라우팅 하여 인터넷 대기시간을 줄이고 전송 선능을 향상하는 서비스
    - 미사용 시 서버로부터 지리적으로 먼 사용자는 많은 인터넷 라우팅을 하여 속도가 느림
    
    ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%2034.png)
    
    - 글로벌 액셀러레이터에는 2개의 Anycast 퍼블릭 고정 IP가 생성됨 (Anycast : 네트워크 트래픽을 가장 가까운 노드로 전송하는 라우팅 방식)
    - Elastic IP, EC2 인스턴스, ALB, NLB 등의 AWS 엔드포인트를 연결하여 사용 가능
    - 애플리케이션의 Health Check 기능을 통해 하나의 서버 장애 발생시 다른 서버로 라우팅 가능
    
    [https://www.notion.so](https://www.notion.so)
    

# 애플리케이션 통합

1. Simple Queue Service(SQS)
    - Queue는 대기한다는 의미
    - SQS는 메세지를 대기하는 기능
    - 애플리케이션 간의 느슨한 결합 제공(decoupling)
    
    ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%2035.png)
    
    - SQS는 Poll 방식으로 메세지를 전송 (Customer가 메세지를 요청하여 받는 방식)
    - Customer 가 메세지를 소비하면 SQS Queue에서는 메세지가 삭제됨
    
    ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%2036.png)
    
    - 표준대기열 vs FIFO 대기열
    
    ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%2037.png)
    
    1. Simple Notification Service(SNS)
        - 메세지 전송 서비스
        - 게시자(publisher)에서 구독자(Sbuscriber, 생산자 또는 소비자)로 메세지를 전송
        - 애플리케이션 간(A2A) 및 애플리케이션과 사용자 간(A2P) 통신
        
        ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%2038.png)
        
        1. Kinesis
            - 실시간 스트리밍 데이터를 손쉽게 수집, 처리 및 분석 하는 서비스
            - kinesis 서비스 유형
                - Kinesis Data Streams: 데이터 스트림을 수집, 저장 및 처리
                - Kinesis Data Firehose: 데이터 스트림을 AWS 데이터 스토어에 로드
                - Kinesis Data Analytics: SQL 또는 Apache Flink로 데이터 스트림 분석
                - Kinesis Video Streams: 비디오 스트림을 수집, 저장 및 처리
        
        1. API Gateway
            - 개발자가 API를 생성, 게시, 유지관리, 모니터링 및 보안유지를 할 수 있게 하는 서비스 (API : Application Programming Interface)
            - 예) 애플리케이션 API를 통해 백엔드 시스템 및 데이터에 액세스 하여 통신
                
                ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%2039.png)
                

# 보안, 자격 증명 및 규정 준수

1. AWS 공동 책임
    
    ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%2040.png)
    
    ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%2041.png)
    
    1. Shield
        - AWS웹 애플리케이션을 DDos(Distributed Denial of Service) 공격으로부터 보호
        - Shield Standard : 모든 사용자에게 적용(무료), SYN/UDP Flood등 기본적인 DDoS공격 보호
        - Shield Advanced : 스탠다드보다 더 많은 보호 제공 (유료), EC2, ELB, CloudFront, Route53등에서 정교한 DDoS 보호제공
    
    1. WAF (Web Application Firewall)
        - 웹 애플리케이션을 보호하는 방화벽
        - Application Load Balancer, API Gateway, CloudFornt에 적용 가능
    
    1. Key Management System (KMS)
        - 암호화 키를 생성 및 관리하는 서비스
        - KMS는 AWS에서 관리하는 소프트웨어 방식의 암호화
        - AWS에서 암호화에 관련된 서비스는 대부분 KMS와 관련됨
        - 3가지 유형의 키 제공
            - **고객 관리형 키(Customer managed keys)**
                - 사용자가 생성, 소유 및 관리하는 AWS 계정의 KMS 키
                - 키 정책, IAM 정책 및 권한 부여, 암호화 구성요소 등의 제어 권한을 사용자가 가짐
            - **AWS 관리형 키(AWS managed keys)**
                - AWS 서비스가 고객의 계정에서 고객 대신 생성, 관리 및 사용하는 KMS 키
                - 키 정책, 키 삭제 등의 제어 권한이 없거나 제한이 있음
            - **AWS의 키(AWS owned keys)**
                - AWS 서비스가 여러 AWS 계정에서 사용하기 위해 소유하고 관리하는 KMS 키 모음
                
    2. CloudHSM
        - CloudHSM은 AWS에서 제공하는 하드웨어 암호화 장비를 통한 하드웨어 방식의 암호화
        - KMS와 다르게 암호화 관리는 사용자(클라이언트)가 해야함
    
    1. AWS Certificate Manager(ACM)
        - SSL/TLS 인증서를 중앙에서 관리하는 서비스
    
    1. Secrets Manager
        - 보안 정보(자격증명)를 중앙 집중식으로 저장, 검색, 액세스 제어, 교체, 감사 및 모니터링 하는 서비스
        - 보안정보(자격증명, Scret)를 유지하는 방법
            - 사용자가 소유하고 AWS Key Management Service(KMS)에 저장한 암호화 키를 사용해 저장 보안 정보를 암호화
            - 사용자는 AWS Identity and Access Management(IAM) 정책을 사용하여 보안 정보에 대한 액세스를 제어
            - 사용자가 보안 정보를 검색하면 Secrets Manager가 해당 보안 정보를 복호화하여 TLS를 통해 안전하게 로컬 환경으로 전송
    2. AWS Artifact
        - AWS의 규정 준수 문서와 AWS 계약에 대한 문서를 제공하는 사이트
        - 실제 서비스가 아니라 문서를 보고 다운받을 수 있는 사이트
    
    1. GuardDuty, Macie, Inspector
        1. GuardDuty
            - AWS 계정 및 워크로드에서 악의적 활동을 모니터링 하고 상세한 보안 결과를 제공하는 위협 탐지 서비스
        2. Amazon Macie
            - 데이터 보안 및 데이터 프라이버시 서비스로서, 기계학습 및 패턴 일치를 활용하여 AWS에서 민감한 데이터를 검색하고 보호
        3. Amazon Inspector
            - Amazon Elastic Compute Cloud(EC2) 및 컨테이너 워크로드에서 소프트웨어 취약성과 의도하지 않는 네트워크 노출을 지속적으로 스캔하는 자동화된 취약성 관리 서비스
    2. Securit Hub
        - AWS에서 보안 상태에 대한 통합 보기를 제공
        - AWS환경에서 보안 검사를 자동화하고, 보안분석 결과를 관리하며, 우선순위가 가장 높은 보안 문제를 식별
            
            ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%2042.png)
            
        1. Amazon Detective
            - 잠재적 보안 문제나 의심스러운 활동의 근본 원인을 쉽고 빠르게 분석, 조사 및 식별하는 서비스
            - Amazon GuardDuty, Amazon Macie 및 AWS Security Hub는 잠재적 보안 문제나 탐지 결과를 식별 하여, 문제가 발생했음을 알리거나 수정할 위치를 가리킬 때 매우 유용
        
        1. AWS Abuse
            - 악의적이거나 불법적인 용도로 AWS 리소스가 사용되고 있다고 의심될 경우 AWS에 알릴 수 있음
        2. AWS Cognito
            - 애플리케이션에 대한 로그인 및 인증을 제공하는 기능
        3. AWS Single Sign ON (SSO)
            - SSO는 중앙에서 관리하는 하나의 계정으로 여러 애 플리케이션에 로그인 하는 기능

# 관리 및 거버넌스

1. CloudWatch
    - AWS 클라우드 리소스와 AWS에서 실행되는 애플리케이션을 위한 모니터링 서비스
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

1. CloudTrail
    - AWS 계정이 수행하는 작업에 대해 로그를 기록하는 서비스
    - AWS계정의 거버넌스, 규정준수, 운영감사, 위험감사에 활용
2. Config
    - AWS 리소스 구성 변경 사항을 로그기록 하는 기능
    - 수집된 로그는 분석, 보안감사를 위해 S3 버킷으로 저장가능

1. System Manager(SSM)
    - 서버의 운영 데이터를 수집하는 기능
    - 보안패치 업데이트, 방화벽 정책 등의 작업을 자동화
    - SSM Session Manager
        - EC2 또는 온프레미스 서버에 대한 원격 연결 가능
        
2. AWS Service Health Dashboard
    - AWS 전체 리전, 서비스에 대한 상태를 알려주는 서비스
    - 일반적인 AWS 서비스 상태를 확인
3. AWS Personal Health Dashboard
    - 사용자 AWS 계정에서 사용하는 특정 AWS 서비스의 상태에 대해 개인화된 보기를 제공
    - 본인의 AWS 계정에 영향을 줄 수 있는 진행중이거나 예정된 특정 이벤트에 대한 알림 생성 기능
4. Trusted Advisor
    - 사용자 AWS 환경을 조사하여 비용 절감, 시스템 성능 향상 또는 보안 결함 제거를 위한 권장 사항을 제시
    - 비용최적화, 성능, 보안, 내결함성, 서비스한도 5가지 카테고리를 검사
        - 비용최적화
            - 사용되지 않는 유휴 리소스를 제거하거나 예약 용량을 약정하여 AWS에서 비용을 절약할 수 있는 방법을 확인
            - 사용률이 낮거나 사용하지 않는 유휴상태의 EC2, Load Balancer, RDS, 탄력적 IP 주소 등
        - 성능
            - 서비스 한도를 점검하고, 프로비저닝 된 처리량을 활용하고 확인하고, 과다 사용되는 인스턴스를 모니터링하여 서비스 성능을 개선
        - 보안
            - 결함을 없애고, 다양한 AWS 보안 기능을 사용하며, 권한을 점검하여 애플리케이션 보안을 개선
        - 내결함성
            - Auto Scaling, 상태확인, 다중AZ 및 백업 기능을 활용하여 AWS 애플리케이션의 가용성과 중복성을 높임
        - 서비스한도
            - 서비스 한도의 80%가 넘는 서비스 사용량이 있는지 점검
5. AWS Organizations
    - 여러 AWS 계정을 중앙에서 관리
    - 글로벌 서비스
    - 계정을 통합하면 결제를 한곳으로 통합 가능하고 볼륨 가격 할인을 받을 수 있음 (통합결제)

# 개발자도구

1. CodeCommit
    - git을 이용해 코드 변경사항(버전)을 관리하는 서비스
2. CodeDeploy
    - 소프트웨어(코드) 배포를 자동화하는 서비스
3. CodeBuild
    - 소프트웨어(코드)를 빌드하는 서비스
4. CodePipeline
    - 소프트웨어(코드) 릴리스 파이프라인을 자동화 하는 서비스 (빌드 → 테스트 → 배포 단계를 자동화하는 서비스)
5. CodeArtifact
    - 소프트웨어 패키지를 안전하게 저장, 게시 및 공유할 수 있도록 지원하는 완전관리형 아티팩트 리포지토리 서비스
6. CodeStar
    - 소프트웨어 개발 활동을 한곳에서 쉽게 관리 하는 서비스
    - 애플리케이션 코드의 코딩, 빌드, 테스트 및 배포 위한 전체 개발 및 지속적 전달 도구 체인을 간편하게 구성
7. Cloud9
    - 클라우드 기반 IDE 서비스(Integrated Development Environment)
    - 코드를 작성, 실행, 편집 하는 도구
8. X-ray
    - 데스크톱 브라우저 및 실제 모바일 디바이스에서 테스트를 진행하여 웹 및 모바일 앱 품질을 향상시키는 애플리케이션 테스트 서비스
9. Falut Injection Simulator
    - 오류 주입 실험을 수행하기 위한 완전관리형 서비스 (어플리케이션에 스트레스 유발 등)

# 머신러닝

1. Comprehend
    - 텍스트 안에서 특정 항목을 찾아내는 서비스
2. Rekognition
    - 이미지, 비디오 분석
3. Polly
    - 텍스트를 음성으로 변환하는 서비스
4. Lex
    - 음성인식 서비스, 챗봇 구현 가능
5. Textract
    - 스캔문서에서 문자, 테이블, 양식 추출 서비스
6. Translate
    - 번역 서비스
7. Transcribe
    - 음성을 텍스트로 변환
8. SageMaker
    - 머신러닝 모델을 구축, 훈련 및 배포하는 서비스
9. Forecast
    - 머신러닝을 기반으로 하며, 비즈니스 지표 분석을 위해 구축된 시계열 예측 서비스
10. Kendera
    - 지능형 검색 서비스
11. Personalize
    - Amazon.com에서 실시간 맞춤화 추천에 사용하는 것과 동일한 기계학습(ML) 기술로 애플리케이션 구축 가능한 서비스
12. Amazon Connect
    - 클라우드 기반 고객 센터 서비스

# 인프라 자동화

1. CloudFormation
    - 코드를 통해 인프라를 프로비저닝, 관리하는 서비스(Infrastructure as Code)
    - 코드를 통해 자동화 하여 AWS 인프라를 생성, 업데이트, 삭제 기능

# AWS 비용관리

1. AWS Budgets(예산)
    - 예산을 지정하여 비용과 사용량을 추적하는 서비스
    - 비용 또는 사용량이 사용자가 지정한 임계값을 초과할 때 이메일 등으로 알림을 받거나 RDS /  EC2 등의 서비스를 중지하는 작업을 연결할 수 있음
    - 비용할당 태그를 이용해 AWS특정 리소스에 태그 값을 지정하여 태그에 대한 리소스 보고서만 생성 가능 (ex) 특정 애플리케이션을 실행하는 서비스비용과 사용량에 대한 보고서 생성 가능
2. AWS Cost Explorer (비용탐색기)
    - AWS 서비스에 대한 비용 및 사용량을 분석하는 서비스
    - 서비스별, 계정별로 일별, 월별 사용량 및 비용을 확인하여 보고서를 생성 및 다운로드 할 수 있음
    - Cost Explorer는 그래프, 숫자를 통한 시각화 된 인터페이스를 제공
3. AWS Pricing Calculator
    - AWS 서비스 사용에 대한 예상 비용을 계산하는 서비스

# AWS 기술지원

1. AWS Support Plan
    - AWS에서는 기본, 개발자, 비즈니스, Enterprise On-Ramp, 엔터프라이즈 5가지 플랜을 제공
        - **AWS Trusted Advisor** - 핵심 Trusted Advisor 확인 및 지침에 액세스 ➢ 보안 그룹 – 제한 없는 특정 포트(무료) ➢ AWS IAM 사용(무료) ➢ Amazon S3 버킷 권한(무료) ➢ 루트 계정의 Multi-Factor Authentication(MFA)(무료) ➢ Amazon RDS 퍼블릭 스냅샷(무료) ➢ 서비스 한도(무료)
    - 기본 지원(Basic Support) 플랜은 모든 AWS 고객에게 제공 되며 아래를 포함
        - **고객 서비스 및 커뮤니티** - 고객 서비스, 설명서, 백서 및 AWS re:Post에 대한 연중무휴 24시간 상시 액세스를 제공
        - **AWS Personal Health Dashboard** - AWS 서비스의 상태를 보여주는 개인화된 보기이며 리소스가 영향을 받을 때 알림을 표시
    
    ![Untitled](AWS%20Certified%20Cloud%20Practitioner%207142adb88f024bc5a83bea2358937135/Untitled%2043.png)
    

# AWS Well-Architected Framework

- 애플리케이션에 사용할 보안, 성능, 복원력 및 효율성이 뛰어난 인프라를 구축하는 클라우드 아키텍트를 돕기 위한 프레임 워크
- 여섯가지 원칙을 기반
    - 운용 우수성(Operational Excellence)
    - 보안 원칙(Security)
    - 안정성/신뢰성 원칙(Reliability)
    - 성능 효율성 원칙(Performance Efficiency)
    - 비용 최적화 원칙(Cost Optimization)
    - 지속 가능성 원칙(Sustainablilty)