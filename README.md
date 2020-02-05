

# About nanaones

# Work Experience
  
  
## WAS Develop & Maintenance
* ICON Tracker (Back-end) (https://tracker.icon.foundation/) --  [LINK](https://github.com/nanare/resume#icon-tracker-back-end-httpstrackericonfoundation)
* ICON FoundationHomePage (https://icon.foundation/?lang=en) --  [LINK](https://github.com/nanare/resume#icon-foundationhomepage-httpsiconfoundationlangen)
* TxChallenge DashBoard Page Back-End (deprecated) --  [LINK](https://github.com/nanare/resume#txchallenge-dashboard-page-back-end)

## Public BlockChain
* ICON(Public BlockChain) SmartContractAudit  --  [LINK](https://github.com/nanare/resume#iconpublic-blockchain-smartcontractaudit)
* ICON SmartContractAuditTool Develop --  [LINK](https://github.com/nanare/resume#icon-smartcontractaudit-tool-develop)
* Blockchain training course for developers.   --  [LINK](https://github.com/nanare/resume#blockchain-training-course-for-developers)

# Side Project  
TBD

---

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
포항공대 Mooc BlockChain Course 진행
[YouTube] https://www.youtube.com/playlist?list=PLXXmA0nccv9osZU0KERA3VvndG-TwVfVe

ICON Workshops for Developer 진행
[GitHub] https://github.com/icon-workshops

Devstamp 발표
[GitHub] https://github.com/icon-workshops/181218-devstamp

StudyPie ICON BlockChain 진행

---

## icon
