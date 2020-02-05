
# Work Experience
## Develop & Maintenance
* ICON Tracker (Back-end) (https://tracker.icon.foundation/) --  [LINK](https://github.com/nanare/resume#icon-tracker-back-end-httpstrackericonfoundation)
    - Java(1.8) Spring
    - Tomcat
    - MySQL, Mybatis

* ICON FoundationHomePage (https://icon.foundation/?lang=en) --  [LINK](https://github.com/nanare/resume#icon-foundationhomepage-httpsiconfoundationlangen)
    - Java(1.8) Spring
    - Tomcat
    - MySQL(AWS RDS), Mybatis

* TxChallenge DashBoard Page Back-End (deprecated) --  [LINK](https://github.com/nanare/resume#txchallenge-dashboard-page-back-end)
    - python
    - gunicorn
    - PostgreSQL, Psycopg

## Public BlockChain
* ICON(Public BlockChain) SmartContractAudit  --  [LINK](https://github.com/nanare/resume#iconpublic-blockchain-smartcontractaudit)
* ICON SmartContractAuditTool Develop --  [LINK](https://github.com/nanare/resume#icon-smartcontractaudit-tool-develop)
    - python
    - pylint, astroid
* Blockchain training course for developers.   --  [LINK](https://github.com/nanare/resume#blockchain-training-course-for-developers)

* 조력발전소 운영에 따른 해양물리변화 장기 조사연구  --  [LINK](https://github.com/nanare/resume#조력발전소-운영에-따른-해양물리변화-장기-조사연구)
    - 결측값 처리

# Side Project  

## Psycopg-test  --  [LINK](https://github.com/nanare/resume#psycopg-test)  
- python
- Docker

## Psycopg-test-docker-compose  --  [LINK](https://github.com/nanare/resume#psycopg-test-docker-composee)  
- python
- PostgreSQL
- Docker-compose, ElasticSearch, Fluentd, Prometheus, Grafana, Kibana, Fluentd-exporter(Fluentd, PostgreSQL)

## 카카오톡 납품관리기  --  [LINK](https://github.com/nanare/resume#카카오톡_납품관리기)
- Python
- PostgreSQL
- PIL
- Flask


---

# Detail

# 1. Work Experience

### TxChallenge DashBoard Page Back-End

 비동기 WAS 적용 및 비동기 배치 적용

Language: Python  
FrameWork: Flask(Python)  
DBMS: PostgreSQL  
Middle Ware: gunicorn & gevent worker
WebServer: Nginx  
gunicorn & gevent Based Asynchronous RESTful API  
이벤트 기간 내, 70,000,000 Tx Count

관여한 핵심기술
- NginX, gunicorn(gevent worker)을 도입하여 API 의 RPS(Requests Per Secound)를 기존의 4배로 향상시킬 수 있었습니다. 
- NginX를 도입하면서, 비동기로 동작하는 WAS의 구현 방법과 모니터링 방법, 성능 최적화에 대한 내용을 배울 수 있었습니다.
- PostgreSQL 을 사용하여 Transaction 데이터를 기록하였습니다.
- Python Async방식의 Batch 프로그램을 활용한 DB 축적 (aiohttp, Psycopg 사용)

프로젝트 수행시 경험한 것
- 참여 개발 팀이 250 팀이 되면서, 각기 팀들은 참여 현황을 확인하기 위해서 API Endpoint의 URI 를 통해 데이터를 추출해 가는 상황이 발생하였습니다. (Nginx Log를 통해 확인) 이에따라 호출 요청이 기하급수적으로 늘어나게 되어 t3.micro 로는 감당할 수 없게 되어 업스케일링을 진행하였습니다. 
- gevent worker 에서 일어나는 Memory Leak(메모리 누수) 현상에 대한 조치를당시에는 취하지 못하였는데, 프로젝트를 회고하는 기간에 gevent github issue 중에서 Memory Leak 관련 내용을 확인하고 수정하게 되었습니다. 시간이 좀 더 있었다면, 각 프로세스별 --max-requests, jiter count를 수정하여 최적의 옵션을 테스트를 통해서 설정했을 것 같습니다. 
- 특정 API는 async 방식에서는 효율적이지 않았습니다. 이는 당시에는 알지 못하였지만 CPU 연산을 고려하지 않은 API 설계가 원인이었습니다.  
회고 : https://github.com/nanaones/Record/blob/master/Python/Gunicorn.md

---

### ICON Tracker (Back-end) (https://tracker.icon.foundation/)
Language: Java(1.8)  
FrameWork: Spring  
WebServer: tomcat  
DBMS: MySQL  
RESTful API maintenance

---

### ICON FoundationHomePage (https://icon.foundation/?lang=en)
Language: Java(1.8)  
FrameWork: Spring  
WebServer: tomcat  
JSP Page maintenance  

---

### ICON SmartContractAudit Tool Develop  
ICON Network에 등록되는 SmartContract의 정적 분석을 수행하는 Audit Tool 개발 ( Back-end, AWS Part )


Language: Python  
Library: pylint, astroid   
Tool: Docker, AWS(AppSync, Lambda, S3, DynamoDB)   


관여한 핵심기술
- BlockChainMainnet과 Docker Container , DynamoDB에서 데이터를 가지고 오는 resolver를 작성하였습니다.
- Tool을 Dockerize하여 관리하였으며, Flask를 통하여 API를 구축했습니다.
- 카나리배포 방법론을 적용하여 GitLab의 runner를 통해 Ci/CD 환경을 구축하였습니다. 
-  Pylint의 BaseChecker를 상속받는 AstroidChecker를 만드는 작업을 통해, 스크립트 언어의 동작 방식에 대해 이해했습니다.

프로젝트 수행시 경험한 것
1. Dockerize  
 Flask를 사용한 API를 작성하였을때, Key와 같은 민감한 데이터는 모두 Configparser 라이브러리를 사용하여 config.ini 로 불러왔지만, 사용되는 설정옵션이 분리되어 관리의 용이성이 떨어지고, 가독성이 떨어져, WAS를 Dockerize 할 때 에는 Dockerize 라이브러리를 사용하여 Docker Ccontainer의 환경변수로 설정하였습니다.
2. Ci/CD  
 만들어진 WAS 에 각 EndPoint 마다 Apache Bench 를 사용한 테스트가 이루어졌습니다. AB의 결과를 Slack으로 보내주며, 사용자의 승인에 의해서 카나리 Server에 배포되며, 일정기간 테스트가 끝나면 MainServer에 배포했습니다. 

---

### ICON(Public BlockChain) SmartContractAudit

ICON Network에 등록되는 SmartContract의 검사수행  
SmartContract의 Logic과 Contract의 무결성 검사수행

BlockChain Mainnet에 Deploy되는 SmartContract의 논리적, 구조적 결함은 Mainnet에 영향을 끼칠 수 있으므로 배포된 SmartContract가 BlockChain Mainnet에 영향을 끼칠 가능성을 보조지표를 참조하여 육안으로 검사를 수행했습니다.

프로젝트 수행시 경험한 것
-  Python은 3.3 이후부터 내장된 hash() 함수의 로직이 일부 바뀌게 되었습니다. 따라서, 이전과는 달리, 실행할 때 마다 다른 값을 출력합니다. 이로인해 hashlib 라이브러리를 통한 hash 값 생성을 권유하였습니다.

---

### Blockchain training course for developers.
포항공대 Mooc BlockChain Course 기획, 제작, 진행
[YouTube] https://www.youtube.com/playlist?list=PLXXmA0nccv9osZU0KERA3VvndG-TwVfVe

ICON Workshops for Developer  기획, 제작, 진행
[GitHub] https://github.com/icon-workshops

Devstamp 발표
[GitHub] https://github.com/icon-workshops/181218-devstamp

StudyPie ICON BlockChain  기획, 제작, 진행

---

### 조력발전소 운영에 따른 해양물리변화 장기 조사연구
Matlab을 이용한 해양 관측 자료의 결측 값 처리 
실제 관측 지원

관여한 핵심기술
- 결측값 처리
    총 데이터중 결측값의 양에따른 의사결정
    총 데이터중 결측값의 상관관계에 따른 의사결정

프로젝트 수행시 경험한 것
- 결측치의 비율에 따른 처리방법론 hair et al.(2006)에 대한 이해


# 2. Side Project


## Psycopg-test 

1. 동일조건에서 ConnectionPool을 사용하지 않고 반복되는 쿼리를 수행했을때, connection의 반복수행으로 인한 overhead로 일어나는 TimeLoss를 확인하기 위한 test입니다.  
2. 동일 조건에서 SingleThreadConnecionPool과 multithreadedConnectionPool의 성능을 비교해보기 위한 test입니다.


repo address:  
https://github.com/nanaones/psycopg-test  

Language: Python  
Library: Psycopg,  configparser, pytz  
Tool: Docker


관여한 핵심기술
- Dockerize  
- Psycopg ConnectionPool
- logging
    - JSON
    - CSV

프로젝트 수행시 경험한 것
1. TimeZone   
    ElasticSearch에 time 태그를 통해서 데이터를 시계열로 저장하기 위해 time 라이브러리를 사용한 Logtime 을 기록하려 하였으나, TimeZone이 설정되어있지 않아 GMT 기준으로 시간이 설정되었습니다. pytz 라이브러리를 홯용하여 TimeZone을 맞추었습니다. 또한, 옵션을 통한 커스터마이징 기능을 구현하였습니다. 
2. JSON  
    시작시간에서 현재시간을 차감한 실제 소요시간을 String으로 지정하여 log를 불러오는데 문제가 있었습니다. json라이브러리의 dump 모듈을 통해서 json 파일을 남기는것으로 수정하였습니다.
3. getenv  
    configparser 라이브러리를 통해  config를 불러옵니다. Dockerize를 하면서 설정에 충돌이 일어나게 되었고, 이를 해결하기 위해서 configfile의 위치를 os의 환경변수에서 먼저 찾도록 수정하였습니다. 

## Psycopg-test-docker-compose  

psycopg-test 가 작업을 수행한 후 남는 로그 파일에 대한 실시간 분석을 위한 Docker-Compose 입니다.   
Prometheus와 Prometheus-exporter(Fluentd, PostgreSQL)가 포함되어있어,  PostgreSQL container의 상태 변화를 실시간으로 확인할 수 있습니다. 

repo address:  
https://github.com/nanaones/psycopg-test-docker-compose 

Language: Python  
Library: Psycopg, configparser, pytz  
Tool: Docker-compose, ElasticSearch, Fluentd, Prometheus, Grafana, Kibana, Prometheus-exporter(Fluentd, PostgreSQL)


관여한 핵심기술
- Compose system architecture  
    Compose의 system architecture를 설계하였습니다.

- Prometheus-exporter( PostgreSQL,  Fluentd )
    Client단에서의 속도를 확인했던 psycopg-test와는 다르게, 속도 그래프의 시각화와는 별개로 PostgreSQL Container가 받는 부하또한 시각화를 통하여 실제 네트워크 전체가 받는 부하를 파악하고 싶었습니다. 

프로젝트 수행시 경험한 것
1. Prometheus Fluentd exporter  
    링크 : https://github.com/fluent/fluentd-docs-gitbook/pull/119  
    공식 Guide 대로 exporter를 설정하였으나, log에서 parameter error가 발생되는 것을 확인하였고, 이는 패키지의 의존성 문제임을 확인하였습니다. 이에따라 수정한 PullRequest를 Fluent repo에 push 하였으며, 이 수정이 반영되었습니다.
    
2. elasticsearch  
    elasticsearch가 부하를 견디지 못하고 Down 되는 경우가 족족 발생하였습니다. 이는 결국 EVM의 메모리가 부족한 현상임을 알게 되었고, bootstrap.memory_lock을 통해서 메모리가 스왑되는 현상을 막았고, ES_JAVA_OPTS을 2GB로 강제 할당하여 자동 종료를 막았습니다.

3. 환경변수  
    Psycopg-test 에서 사용되는 변수들을 Dockerize 하면서 환경변수화 하였습니다. 단독으로 사용될때와 Compose에서 사용될 때 입력될 DBMS의 주소가 달라지기 때문에, 이를 환경변수로 받을 수 있도록 재수정하였습니다. 

4. wait-for-it  
    단독으로 사용되지 않는경우, Psycopg-test Container는 PostgreSQL Container가 올라온 이후에 실행되어야 합니다. 하지만 docker-compose는 순차적으로 Container를 실행시키는 옵션이 따로 존재하지 않습니다. 따라서 wait-for-it 이라는 3rdParty 스크립트를 통해 Psycopg-test Container에 부여된 DBMS 환경변수인 $DBMS_PORT,  $DBMS_ADDRESS 들로 DBMS Container의 정상 실행 유무를 확인하여, 정상적인 응답 유무에 따라 Psycopg-test Container가 실행되도록 하였습니다. 


## 카카오톡 납품관리기 

소상공인을 위한 납품관리기입니다.
카카오톡 플러스친구에게 거래처에 납품한 이미지를 전송하게 되면 전송된 이미지의 좌표(Lon, Lat)를 사진의 EXchangable Image File format(EXIF)에서 읽어들입니다. 전송된 이미지는 서버에 별도로 저장되며, 이미지의 저장위치와 이미지의 좌표(Lon, Lat)은 DBMS에 저장됩니다.

Language: Python  
FrameWork: Flask
Library: Psycopg, PIL, pytz  
Tool: Docker

관여한 핵심기술
- System architecture  
    System architecture를 설계하였습니다.

- 이미지 데이터와 위치정보의 저장  
    카카오톡 API에 업로드된 이미지 데이터를 서버에 저장함과 동시에 위치정보(Lon, Lat)을 저장합니다. urllib 라이브러리를 통해서 작성되었습니다. 

- WAS 개발  
    Flask를 활용한 WAS를 개발하였습니다. 

- DB Table 설계  
    DBMS 선정과 Table을 직접 설계했습니다.


프로젝트 수행시 경험한 것

GPS 측정 오차  
   이미지 파일의 EXIF 데이터에 입력되는 GPS 정보는 핸드폰이 현재 위치를 GPS 위성신호에 따라 측정한 정확도 있는 정보일 수 있지만, 빌딩이 많거나, 주변에 장애물이 많은경우, 지하인 경우에는 GPS 정보가 정확하지 않았습니다. 이에따라 초기에 기획하였던 GPS 위치를 기반으로 업체를 추정하여 기록하는 방식은 포기하게 되었습니다.

[서버저장기 image](https://github.com/nanare/resume/blob/master/img/%EC%84%9C%EB%B2%84%EC%A0%80%EC%9E%A5%EA%B8%B0_%EC%88%98%EC%A0%95.jpg)
