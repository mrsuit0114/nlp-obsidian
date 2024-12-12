# Online Serving
- Online Serving의 구현
	- 직접 웹 서버 개발
		- Flask, FastAPI 등을 사용해 서버 구축
	- 클라우드 서비스 활용
		- AWS(sagemaker), GCP(vertex ai)
		- 활용만 하면됨, 러닝커브를 극복하면 유용
		- 자유도가 떨어지고 내부 구현 방식 확인 불가
	- 오픈소스 활용
		- Torch Serve, MLFlow, Tensorflow Serving
	- Online Serving에서 고려할 것
		- Docker 사용
		- Latency -> 모델 경량화, 병렬 처리, 예측 결과 캐싱, 데이터 전처리 서버 분리
# Server 아키텍처
- 모놀리스 아키텍처
	- 하나의 큰 서버로 개발
	- 장점
		- 단순하고 직관적
	- 고민할 점
		- 모든 서비스 로직이 하나의 저장소에 저장
		- 너무 커지면 복잡함
		- 의존성 및 환경 통일
	- Usecase
		- 서비스 초기, 개발자 부족, 코드의 복잡성이 크지 않은 경우
- 마이크로서비스 아키텍처
	- 작은 여러개의 서버로 개발
	- 장점
		- 거대한 코드 베이스를 작게 나눌 수 있음
		- 필요에 따라 각 서버 단위로 스케일링이 가능
		- 의존성 및 환경 독립적
	- 고민할 점
		- 전체적인 구조와 통신이 복잡해짐 (ex. DB)
	- Usecase
		- 서비스가 고도화되고 개발팀이 큰 경우
		- 서비스별로 독립된 환경과 스케일링이 필요한 경우
# API
- Web API
	- HTTP : 정보를 주고 받을 때 지켜야하는 통신프로토콜
	- 종류
		- REST, GraphQL, RPC
	- REST API
		- 자원을 표현하고 상태를 전송하는 것에 중점을 둔 API
		- REST라고 부르는 아키텍처 스타일로 HTTP 통신을 활용하는 것
		- 요청의 모습을 보고 어떤 일을 하는지 알 수 있음
		- Resource : 고유한 ID를 가지는 리소스 - URI
		- Method : 서버에 요청을 보내기 위한 방식 - GET, POST, PUT 등
		- URL : Uniform Resource Locator - 인터넷 상 자원의 위치
		- URI : Uniform Resource Identifier - 인터넷 상의 자원을 식별하기 위한 문자열의 구성
# REST API
- REST API 사용 예시
	![[Pasted image 20241212220034.png]]
- URL Parameters
	- Query Parameter
		- URL의 끝에 추가하며, 특정 리소스의 추가 정보를 제공 또는 데이터를 필터링할 때 사용 - ex. ?name=abc
	- Path Parameter
		- 리소스의 정확한 위치나 특정 리소스를 찾을 때 사용 - ex. books/{bookId}
- HTTP Header, Payload
	![[Pasted image 20241212220655.png]]
	- -H : header, -d : Payload
- Status Code
	![[Pasted image 20241212220800.png]]
- IP : 네트워크에 연결된 특정 PC의 주소를 나타내는 체계
- Port
	![[Pasted image 20241212220941.png]]