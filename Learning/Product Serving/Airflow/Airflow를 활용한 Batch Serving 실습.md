# 1. 강의 소개

- 이번 시간에는 Batch Serving(Airflow) 실습 시간입니다. Apache Airflow를 코드 단위로 실습하고, DAG을 만드는 연습을 진행합니다. 총 6가지 DAG을 만들고, 마지막 6-simple-elt는 클라우드 실습 영상에서 진행합니다
    
- 이 강의에선 DAG을 어떻게 만드는지, 내가 Airflow로 무엇을 할 수 있을지를 생각하면서 학습해주세요
    - 여러분들이 만든 모델 학습 스크립트를 주기적으로 돌려보는 것도 해보시면 더 활용을 잘 하실 수 있을거에요
- 설치는 로컬 컴퓨터에서 추천합니다. 다만 윈도우의 경우 Docker나 VM을 사용하는 설치를 추천합니다. Docker 실습 영상에 보면 Docker Compose를 사용해 Airflow를 띄우는 예제를 공유했으니 해당 영상을 참고하는 것도 추천드립니다
- 코드는 [다음 링크](https://github.com/zzsza/Boostcamp-AI-Tech-Product-Serving/tree/main/01-batch-serving(airflow))에서 확인할 수 있습니다 :
# 2. 실습 내용 정리
- 환경 구성
	- 가상 환경 설정

    ```
    python -m venv .venv
    source .venv/bin/activate
    ```

	- Apache Airflow 설치
	
	    ```
	    pip3 install pip --upgrade
	
	    AIRFLOW_VERSION=2.6.3
	    PYTHON_VERSION="$(python --version | cut -d " " -f 2 | cut -d "." -f 1-2)"
	    CONSTRAINT_URL="https://raw.githubusercontent.com/apache/airflow/constraints-${AIRFLOW_VERSION}/constraints-${PYTHON_VERSION}.txt"
	
	    pip3 install "apache-airflow==${AIRFLOW_VERSION}" --constraint "${CONSTRAINT_URL}"
	    ```
	
	- Airflow DB init
	
	    ```
	    export AIRFLOW_HOME=`pwd`
	    echo $AIRFLOW_HOME
	
	    airflow db init
	    ```
	
	- Airflow Admin 생성
	
	    ```
	    airflow users create \
	    --username admin \
	    --password 'testadmin' \
	    --firstname riko \
	    --lastname lette \
	    --role Admin \
	    --email woosa0114@gmail.com 
	    ```
	
	- Airflow Webserver 실행
	
	    ```
	    airflow webserver --port 8080
	    ```
	
	- Airflow Scheduler 실행
	
	    ```
	    airflow scheduler
	    ```
---
