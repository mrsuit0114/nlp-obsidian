# 1. Getting Started
- FastAPI 소개
	- FastAPI 특징
		- Node.js, go와 대등한 성능
		- Flask와 비슷한 구조로 마이크로 서비스테 적합
		- Swagger 자동생성, Pydantic -> 생산성 증가
- Poetry
	- pip를 대체하는 패키지 매니저 -> 의존성 잠금 기능이 있음
	- 체계적인 프로젝트 초기화가 가능
	- virtaulenv와 비교해볼 것
- FastAPI - Hello World
	- HTTP Method
		![[Pasted image 20241213154526.png]]
	- localhost:8000
		- localhost:8000/docs, localhost:8000/redoc )=> swagger
	- swagger
		- 만든 API를 클라이언트에서 호출하는 경우 유용 -> FastAPI에서 문서화하여 유지 보수가 용이함
		- 기능 : API 디자인, 빌드, 문서화, 테스팅
# 2. FastAPI 기본 사용법
- URL parameters
	- 어떤 방식을 사용해야 하는가?
		![[Pasted image 20241213155217.png]]
	- Path parameter
		![[Pasted image 20241213155657.png]]
	- Query paramter
		![[Pasted image 20241213155722.png]]
	- Optional parameter
		![[Pasted image 20241213155748.png]]
		![[Pasted image 20241213155841.png]]
	- Request Body
		- 클라이언트에서 API에 데이터를 보낼 때 사용하는 payload
		![[Pasted image 20241213160046.png]]
		![[Pasted image 20241213160105.png]]
	- Response Body
		![[Pasted image 20241213162912.png]]
	- Form
		![[Pasted image 20241213163046.png]]
		- Form(...) : ... 은 필수 요소를 의미
	- File
		![[Pasted image 20241213163509.png]]
		