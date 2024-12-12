# Batch Serving
- Batch Serving의 구현
	- 특성과 사용 예시
		- 일정 기간 데이터 수집 후 일괄 학습 및 결과 제공 -> 모델을 주기적으로 학습시킬 때
		- 수요 예측, 노래 추천
# Apache Airflow 소개
- Batch Processing
	- crontab
		- Airflow이전에 리눅스에서 사용하던 방식
			![[Pasted image 20241212104156.png]]
			- 과거 실행 이력 및 실행 로그를 보기 어렵고 복잡한 파이프라인을 만들기 힘듦, 오류 발생 시 별도의 처리가 없음
			- -> Airflow, prefect, metaflow 등
	- Airflow
		- 주요 기능
			- 파이썬을 사용해 스케줄링 및 파이프라인 작성
			- 스케줄링 및 파이프라인 목록을 볼 수 있는 웹 UI
			- 특정 조건에 따라 작업을 분기할 수 있음
		- 핵심 개념
			- DAGs(Directed Acyclic Graphs) : 작업의 흐름과 순서 정의
			- Operator : 작업 유형을 나타내는 클래스
			- Scheduler : DAGs를 보며 스케줄링
			- Executor : 작업이 실행되는 환경
# Apache Airflow 실습
- 중요 인자
	- catchup
		- true인 경우 시작 날짜로 시작하여 현재 날짜까지 실행 후 계속
		- false인 경우 현재 날짜부터 실행
	- depends_on_past
		- 특정 task가 이전 dag 실행 결과에 의존할지 여부 결정
		- true는 이전 dag가 성공으로 완료되어야 이후의 dag실행 -> 순차적
		- false는 이전 dag의 성공 여부와 상관없이 스케줄이 되면 dag실행 -> 순서무관
- Airflow에서 자주 사용될 Operator와 개념
	- PythonOperator, BranchPythonOperator, BashOperator, DummyOperator(여러task가 다 끝났을 때 확인 용도로 사용가능)
	  SimpleHttpOperator, 클라우드 기능 추상화환 Operator도 존재 (docker, aws, slack 등)
	- variable, connection & hook, sensor, xComs, jinja template
# Airflow 아키텍처 및 활용
- 아키텍처
	![[Pasted image 20241212112100.png]]
	- Scheduler
		- 각종 메타 정보의 기록을 담당
		- DAG dir내 .py 파일에서 DAG를 파싱하여 DB에 저장
		- DAG의 스케줄링 및 담당
		- 실행 진행 상황과 결과를 DB에 저장
		- Executor를 통해 DAG를 실행
	- Executor
		- 스케줄링 기간이 된 DAG를 실행하는 객체
		- Local Executor, Remote Executor
	- Worker
		- DAG의 작업을 수행
	- Metadata DB
		- 파싱한 DAG 정보, DAG run 상태와 실행 내용, task 정보 등을 저장
	- Webserver
		- REST API제공 -> WEB UI 고집할 필요 없음