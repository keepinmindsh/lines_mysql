# DB 설계시 중요한 점 

## Primary Key에 의미를 부여하지 말자 
## NULL을 허용해야 하는지 고려하자 
- Null은 수집되지 못한 데이터를 뜻하기도 한다.  

## 정규화 
- 속성은 반드시 하나의 값을 가져야 한다. ( 제 1 정규화 )

## 데이터 타입 

###  Char

- 입력 문자열의 길이가 일정한 경우 가능한 Char 타입을 사용하며 Varchar2, Varchar 타음은 가급적 사용하지 않는다.
- 디스크 공간의 효율적 활용 및 Insert, Update시 속도 향상과 fragmentation 방지를 위해 Varchar 보다는 Char 타입이 효율적이다.
- Char 타입의 출력 시 Right Trim 처리가 필요할 수 있으므로 주의한다.
- 날짜 혹은 시간을 표현할 경우 Date, DateTime 타입보다는 Char 타입을 사용하도록 한다.

  년월일을 저장할 경우 8자리, 시분초까지 저장할 겨우에는 14자리를 사용한다
  Sample >>
  Char(8)  : 날짜 - YYYYMMDD
  Char(14) : 날짜, 시간 - YYYYMMDDHHMI24SS  

## Tool 추천 

> [MySQL Workbench](https://velog.io/@litiblue/MySQL-Workbench-%EB%A1%9C-DB-%EC%84%A4%EA%B3%84%ED%95%98%EA%B8%B0)