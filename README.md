
# 1. Work Experience
## Technical Stack
Language: Python, Java8  
FrameWork: Flask, SpringBoot  
DBMS: PostgreSQL, MySQL   
Middle Ware: gunicorn & gevent worker  
WebServer: Nginx  
Tools: Docker, AWS(AppSync, Lambda, S3, DynamoDB)  

---

### TxChallenge DashBoard Page Back-End

- Async(비동기) 방식 batch, API Server 개발
  
- 이벤트 기간 내 70,000,000 Tx 처리

- NginX, gunicorn(gevent worker)을 도입하여 API 의 RPS(Requests Per Secound)를 기존의 4배로 향상

  
회고 : https://github.com/nanaones/Record/blob/master/Python/Gunicorn.md

---

### ICON Tracker (Back-end) (https://tracker.icon.foundation/)

블록체인의 정보를 표출해주는 웹 페이지의 Back-end 개발 & 유지보수   

DBMS: MySQL  
RESTful API maintenance

---

### ICON FoundationHomePage (https://icon.foundation/?lang=en)

JSP maintenance  

---

### ICON SmartContractAudit Tool Develop  
ICON Network에 등록되는 SmartContract의 정적 분석을 수행하는 Audit Tool 개발 ( Back-end, AWS Part )

- 카나리배포 방법론을 적용한  Ci/CD 환경 구축으로 서비스 안정성 증대

- 육안검사 실행 전 정적분석 보고서를 통한 검사시간감소 및 위험요소 저감

- Dockerize를 통한 배포로 팀 전체의 생산성 향상

---

### ICON(Public BlockChain) SmartContractAudit

- ICON Network에 등록되는 SmartContract의 검사수행  

- SmartContract의 Logic과 Contract의 무결성 검사수행

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

Matlab을 이용한 해양 관측 자료의 결측 값 처리 및 관측 지원  

- 처리방법론 hair et al.(2006) 적용으로 시스템화 


# 2. Side Project


## Psycopg-test 

1. 동일조건에서 ConnectionPool을 사용하지 않고 반복되는 쿼리를 수행했을때, connection의 반복수행으로 인한 overhead로 일어나는 TimeLoss를 확인하기 위한 test.  
2. 동일 조건에서 SingleThreadConnecionPool과 multithreadedConnectionPool의 성능을 비교해보기 위한 test.


repo address:  
https://github.com/nanaones/psycopg-test  

Language: Python  
Library: Psycopg,  configparser, pytz  
Tool: Docker

---

## Psycopg-test-docker-compose  

psycopg-test 가 작업을 수행한 후 남는 로그 파일에 대한 실시간 분석을 위한 Docker-Compose.   
Prometheus와 Prometheus-exporter(Fluentd, PostgreSQL)가 포함되어있어,  PostgreSQL container의 상태 변화를 실시간으로 확인가능 

repo address:  
https://github.com/nanaones/psycopg-test-docker-compose 

Language: Python  
Library: Psycopg, configparser, pytz  
Tool: Docker-compose, ElasticSearch, Fluentd, Prometheus, Grafana, Kibana, Prometheus-exporter(Fluentd, PostgreSQL), wait-for-it

- Prometheus Fluentd exporter 오류를 수정한 push를 통해 오픈소스 기여  
    링크 : https://github.com/fluent/fluentd-docs-gitbook/pull/119  
    
---

## 카카오톡 납품관리기 

소상공인을 위한 납품관리기 개발

- 사내 시스템구축으로 인한 쳬계 정립

- System architecture 설계

- 이미지데이터 및 위치정보 추출과 저장

- API Server 개발  

- [서버저장기 image](https://github.com/nanare/resume/blob/master/img/%EC%84%9C%EB%B2%84%EC%A0%80%EC%9E%A5%EA%B8%B0_%EC%88%98%EC%A0%95.jpg)
