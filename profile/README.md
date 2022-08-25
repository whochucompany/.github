# ByteClone project
## Summary
- 웹 뉴스레터 "Byte" 클론코딩 프로젝트

# Team
## ⚛FE 
![React](https://img.shields.io/badge/react-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB)
![React Hook Form](https://img.shields.io/badge/React%20Hook%20Form-%23EC5990.svg?style=for-the-badge&logo=reacthookform&logoColor=white)
![React Router](https://img.shields.io/badge/React_Router-CA4245?style=for-the-badge&logo=react-router&logoColor=white)
![Styled Components](https://img.shields.io/badge/styled--components-DB7093?style=for-the-badge&logo=styled-components&logoColor=white)
### 김예림 [FE 리드]
- Main page UI/UX
- Post CRUD
- S3 Deployment
### 구장우
- Login/Signup
- Comment CRUD

## ☢BE
![Spring](https://img.shields.io/badge/spring-%236DB33F.svg?style=for-the-badge&logo=spring&logoColor=white)
![Redis](https://img.shields.io/badge/redis-%23DD0031.svg?style=for-the-badge&logo=redis&logoColor=white)
![Swagger](https://img.shields.io/badge/-Swagger-%23Clojure?style=for-the-badge&logo=swagger&logoColor=white)
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
- Swagger 
   ![image](https://user-images.githubusercontent.com/108961843/186603748-ef8ed878-32cf-48f2-b6e4-b65866d00e15.png)
   
   ![image](https://user-images.githubusercontent.com/108961843/186603778-2020cb11-6c2c-4b86-86ad-ed95f4a07685.png)

- Logging

  ![image](https://user-images.githubusercontent.com/108961843/186603840-7de9d74f-1ea8-4ddb-8477-85c86ad4f69b.png)
  
  ![image](https://user-images.githubusercontent.com/108961843/186603864-cd66b6f7-1b67-4fc4-a0a2-3fea90271e50.png)


- Reids 상세설명(레디스 캐싱 전략)
   
   우선 읽기 전략만을 사용하였으며
   
   ![image](https://user-images.githubusercontent.com/108961843/186596308-bb4cbf96-840d-40c5-b5c1-f2504181f331.png)
   
  1.캐시를 우선적으로 확인
  
  2.캐시에 있으면 해당 데이터를 읽음
  
  3.없다면 DB에 접근해 데이터를 가지고 온 뒤, 캐시에 저장 (Lazy Loading)
    불가피하게 작성자가 수정 및 삭제가 발생하면 레디스 캐시도 같이 삭제 되게 구현
  
## Trouble Shooting
### FE
#### useform, 이미지 파일, ck에디터를 사용하여 각각 formdata에 데이터 입력이 안되는 상황
> ck에디터같은 경우 useRef로 dom을 지목한 뒤, 값을 가져오고, 이미지 같은 경우 useState로 넣은 값을 가져와 form에 append 시켜줌

#### s3 배포할 때 cli 로 유저 추가한 뒤 배포 과정에서 문제가 생김
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FrsuXF%2FbtqV08o6vRd%2FYflksAddsBKG3B1srw1750%2Fimg.jpg)
> 유저 입력을 잘못했기 때문에 생긴 에러. configure --profile 다시 입력했습니다.

#### 배포 후 XML 에러...
![image](https://trustedmedia.aisingapore.org/media/competition/2021/11/19/16372867237658966Screenshot%20from%202021-11-19%2009-49-39.png)
> ACL(액세스 제어 목록)에서 버킷 ACL 읽기 권한을 부여

#### (아쉬운 점) 게시글 콘텐츠를 출력할 때 태그가 입력이 되지 않고 그대로 출력되는 상황 (해결하지 못함)
>dangerouslySetInnerHTML 를 사용하면 태그를 사용하면 된다고 하지만 xxs에 관련되어있는 것 같아 좀 더 공부한 후에 사용 여부 결정... 다음에는 마크업으로 진행하고 싶음

### BE

#### Redis
> 1. 자주변하는 값들은 캐시에 저장 X
> News 수정이 빈번하지 X >> 레디스에서 저장하고 불러옴<br/>
> Comment 자주 변함 >> access to Main DB
> 2. 레디스 CrudRepository 명령어 관련
> findbyId 됨
> findbyNewId 되지 않음
> 3. 권한설정  
> - Redis 연결할때 demonize yes 확인(백그라운드 실행 관련)
> - 서버 ip, 포트 설정 : bind in 0.0.0.0. 변경
> 4. 레디스는 관계형 데이터 베이스가 아니기 때문에<br/> 
> ex) news.getmember.getusername은 되지 아니함
> 그래서 레디스 엔티티에 연관관계 없이 데이터 변수를 기입

#### (아쉬운 점) 
> 테스트 코드 작성<br/>
> QueryDSL<br/>
> Github Action을 이용한 무중단 배포  
