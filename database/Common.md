# Common
### COUNT(*) vs COUNT(1) vs COUNT(column)
- COUNT(*)과 COUNT(1)은 동일한 수의 블록 읽기 / 쓰기 / 처리 시에 같은 CPU 사용시간, 수행 시간을 갖는다.
- COUNT(column)은 NULL 값이 들어간 행은 카운트하지 않는다.(*과 1은 카운트 한다.)