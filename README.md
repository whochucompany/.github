# ByteClone project
## Summary
- 웹 뉴스레터 "Byte" 클론코딩 프로젝트

# Team
## ⚛FE
### 김예림 [FE 리드]
- Main page UI/UX
- Post CRUD
- S3 Deployment
### 구장우
- Login/Signup
- Comment CRUD

## ☢BE
### 박상욱 [BE 리드]
- 로그인/회원가입, JWT 토큰 발행
- Logging
- Swagger
### 손원철
- Redis 서버 구성
- Comment CRUD
- Deployment
### 구자령
- Post CRUD
- Image upload
- page-nation

## Period
- 2022.08.19 ~ 2022.08.25

## 구현기능
- Login/Signup
- Post CRUD
- Image upload
- Comment CRUD

## Trouble Shooting
### FE

### BE

레디스 트러블 슈팅..
1. 자주변하는 값들은 캐시에 저장안함
News는 자주 안변함 >> 레디스에서 저장하고 불러옴
Comment는 자주 변함 >> 그냥 db에서 불러옴

2. 레디스 CrudRepository 명령어 관련..
findbyId 됨. 
findbyNewId 되지 않음..

3. 권한설정  
- Redis 연결할때 demonize yes 확인(백그라운드 실행 관련)
- 서버ip포트설정 : bind in 0.0.0.0. 변경

4. 레디스는 관계형 데이터 베이스가 아니기 때문에 
 ex) news.getmember.getusername은 되지 아니함.
그래서 레디스 엔티티에 연관관계 없이 데이터 변수를 기입..


