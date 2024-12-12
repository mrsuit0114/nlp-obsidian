- 상황
	- 현재 3.13(최신 버전)이 설치되어있는 상황에서 3.11이 필요하여 가상환경에서 사용하기 위해 3.11을 설치해야 한다.
- 고려사항
	- 이를 설치하면 global환경에서 파이썬을 실행할 때 3.11로 환경변수가 바뀌는지 -> gpt는 바뀔 것으로 예상함
	- brew로 업그레이드 할 때 해당 버전이 유지되는지
- 과정
		``` brew install python@3.11 
- ---
# 결과
- Python3 명령어는 최신버전을 사용하는 것으로 확인됨
    ```
    ~
    ❯ python3
    Python 3.13.1 (main, Dec  3 2024, 17:59:52) [Clang 16.0.0 (clang-1600.0.26.4)] on darwin
    Type "help", "copyright", "credits" or "license" for more information.
    >>>
    ```
    
- Python 3.11을 개별적으로 실행 가능하며, 이 경우 경로는 3.11을 유지:
    ```
    ~ took 5s
    ❯ python3.11
    Python 3.11.11 (main, Dec  3 2024, 17:20:40) [Clang 16.0.0 (clang-1600.0.26.4)] on darwin
    Type "help", "copyright", "credits" or "license" for more information.
    >>> import sys
    >>> sys.path
    ['', '/opt/homebrew/Cellar/python@3.11/3.11.11/Frameworks/Python.framework/Versions/3.11/lib/python311.zip', '/opt/homebrew/Cellar/python@3.11/3.11.11/Frameworks/Python.framework/Versions/3.11/lib/python3.11', '/opt/homebrew/Cellar/python@3.11/3.11.11/Frameworks/Python.framework/Versions/3.11/lib/python3.11/lib-dynload', '/opt/homebrew/lib/python3.11/site-packages']
    >>> ^D
    ```

- Python 3.13의 실행 모습:
    ```
    ~ took 11s
    ❯ python3
    Python 3.13.1 (main, Dec  3 2024, 17:59:52) [Clang 16.0.0 (clang-1600.0.26.4)] on darwin
    Type "help", "copyright", "credits" or "license" for more information.
    >>> import sys
    >>> sys.path
    ['', '/opt/homebrew/Cellar/python@3.13/3.13.1/Frameworks/Python.framework/Versions/3.13/lib/python313.zip', '/opt/homebrew/Cellar/python@3.13/3.13.1/Frameworks/Python.framework/Versions/3.13/lib/python3.13', '/opt/homebrew/Cellar/python@3.13/3.13.1/Frameworks/Python.framework/Versions/3.13/lib/python3.13/lib-dynload', '/opt/homebrew/lib/python3.13/site-packages']
    >>>
    ```