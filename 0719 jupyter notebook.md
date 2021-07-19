# 설치

(바탕화면 우클릭 - git bash here)

폴더 위치 상관없이 

```
pip install jupyter
```

입력

* jupyter notebook과 유사한 서비스: google colab



#### 확장프로그램 설치

1. nbextensions

```
pip install jupyter_contrib_nbextensions
```

실행 후 상단 메뉴 - nbextensions에서

Table of Contents (2) 체크

2. css, js files

```
jupyter contrib nbextension install --user
```

- c 드라이브/사용자/유저네임/.jupyter 폴더 생성 확인



# 실행

```
jupyter notebook
```

git bash에서 실행 후 종료는 ctrl + c



#### 새파일 만들기

우측 NEW 버튼 - Python 3 클릭



#### 사용 방법

파란색 = 커맨드모드(단축키 동작), ESC 누르면 입력모드 전환

초록색 = 입력모드(단축키 동작X)



#### 단축키

|      키       | 기능                                    |
| :-----------: | --------------------------------------- |
|       H       | 단축키 목록 출력                        |
|       A       | 상단 셀 생성                            |
|       B       | 하단 셀 생성                            |
|      DD       | 셀 삭제                                 |
|       X       | 셀 잘라내기                             |
| ctrl + enter  | 현재 셀 실행                            |
| shift + enter | (추천) 실행 + 다음 셀 선택(없으면 생성) |
|  alt + enter  | 실행 + 다음 셀 생성                     |
|       M       | 마크다운 셀로 변경                      |
|       Y       | 코드 셀로 변경                          |
| ctrl + s or S | 저장                                    |



#### 기타

- 삭제 취소: 상단 메뉴 Edit - Undo Delete Cells

- In[]안의 숫자: 실행 순서(카운트)

- In [*]: 실행 중이라는 뜻(렉)

  ​	이 때 중지 누르고 상단 메뉴 Kernel - Restart & Clear Ouput

