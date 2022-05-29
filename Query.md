# SQL Query
## 📌 정의
데이터베이스에 정보를 요청하는 것
## 🔄 특징
웹 서버에 특정한 정보를 보여달라는 웹 클라이언트 요청에 의한 처리
대개 데이터베이스로부터 특정한 주제어나 어귀를 찾기 위해 사용
## 📎 문법
### ✔ 모든 필드(컬럼)를 조회하는 경우
SELECT *
FROM [테이블명]
### ✔ 여러 필드를 조회하는 경우
SELECT [필드명1], [필드명2]
FROM [테이블명]
### ✔ 중복된 데이터를 없애고 조회하는 경우
SELECT DISTINCT [필드명]
FROM [테이블명]
### ✔ 조건식을 적용하는 경우
SELECT *
FROM [테이블명]
WHERE [필드명]=0
### ✔ 여러 조건식을 적용하는 경우
SELECT *
FROM [테이블명]
WHERE [필드명1]=0
AND [필드명2]=0
OR [필드명3]=0
### ✔ BETWEEN (~부터 ~까지)
WHERE [필드명] BETWEEN 0 AND 100
WHERE [필드명] NOT BETWEEN 0 AND 100
### ✔ In (~이거나)
WHERE [필드명] IN (0, 10, 100)
WHERE [필드명] NOT IN (0, 10, 100)
### ✔ IS NULL (필드값이 비어 있는지, 즉 NULL인지 판단)
WHERE [필드명] IS NULL
WHERE [필드명] NOT IS NULL
### ✔ LIKE (~로 시작, 포함, 끝나는 단어)
WHERE [필드명] LIKE '[특정값%]'
WHERE [필드명] NOT LIKE '[%특정값%]'
WHERE [필드명] NOT LIKE '[%특정값]'
### ✔ 특정 필드 기준으로 정렬하는 경우
SELECT [필드명]
FROM [테이블명]
ORDER BY [필드명]
### ✔ 정렬 기준이 여러 개인 경우
SELECT [필드명]
FROM [테이블명]
ORDER BY [필드명1], [필드명2] DESC, [필드명3] ASC
