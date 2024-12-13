# 1. Pydantic 사용법
- Pydantic 소개
	- 파이썬 기본 타입에 대한 검증 지원
		![[Pasted image 20241213172252.png]]
	- Pydantic 기능
		- Validation
		- Config 관리
- Validaion
	- Validation을 할 때 사용할 수 있는 방법
		- 예시로 올바른 url, 1-10 사이의 정수, 올바른 폴더 이름을 조건으로 사용
		- 일반 Python Class 활용
			![[Pasted image 20241213172453.png]]
			- 의미없는 코드가 많아짐
			- 복잡한 검증 로직에서 class method가 복잡함
			- 예외 처리가 복잡해짐
		- Dataclass 활용
			![[Pasted image 20241213172841.png]]
			- 인스턴스 생성 시점에 검증하기 쉬움
			- 여전히 검증 로직을 직접 작성해야함
			- 검증 로직을 따로 작성하지 않으면 런타임에서 type checking을 지원하지 않음
		- Pydantic 활용
			![[Pasted image 20241213173012.png]]
			- 훨씬 간결해지 코드
			- 주로 쓰는 타입들에 대한 검증이 만들어져 있음
			- custom type에 대한 검증도 쉽게 가능
			- 런타임에서 type hint에 따라서 validation error 발생
- Config
	- Config 관리
		- 코드내에서 관리 -> 로컬환경 테스트에만
		- yaml 등과 같은 파일로 관리
			- 별도의 파일에서 관리 후, 실행할 때 파일을 지정해서 Config 클래스에 주입하는 방법
			- 배포 환경 별로 파일을 생성
			- 보안 정보가 여전히 파일에 노출
		- Pydantic.BaseSettings으로 관리
 			![[Pasted image 20241213173540.png]]
# 2. FastAPI 확장 기능
- Lifespan function
	- FastAPI 앱을 실행할 때와 종료할 때 로직을 넣고 싶은 경우
		![[Pasted image 20241213174101.png]]
- API Router
	![[Pasted image 20241213174200.png]]
	![[Pasted image 20241213174325.png]]
- Procject structure
- Error Handler
	![[Pasted image 20241213174615.png]]
	![[Pasted image 20241213174809.png]]
- Background Tasks
	![[Pasted image 20241213174949.png]]
	![[Pasted image 20241213175009.png]]
	![[Pasted image 20241213175111.png]]
# 3. FastAPI가 어렵다면
- 어려운 이유
	- 프로젝트 구조
		- Cookiecutter 사용해보기 -> 개인용 쿠키 커터 템플릿 만들어보기
		- Cookiecutter-fastapi
	- 객체 지향
		- 현재 코드를 class로 변경해보기
		- Pydantic use case 탐색하기