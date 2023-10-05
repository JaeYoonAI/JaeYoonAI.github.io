---
layout: post
title: 상부삼조 팀프로젝트 SA
date: 2023-10-05 17:10:20 +0900
description: SA # Add post description (optional)
img: PJSA.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [DRF, TeamProject, ReviewSite]
---

<h1>1. 프로젝트 명 : Alpha Critic</h1>
저희 팀의 프로젝트인 Alpha Critic은 영화, 음악, 게임의 평점과 간단한 리뷰를 남길 수 있는 서비스입니다.



<h1>2. 와이어프레임</h1>

<img src="/assets/img/PJSA.png" width="620" height="314">

<h1>3. ERD 설계</h1>
<img src="/assets/img/ERD_3b3j.png" width="620" height="314">


<h1>4. 개발해야 하는 기능, API 명세</h1>
1. 회원기능
   1. 내가 리뷰한 목록 보기
   2. jwt토큰 이용해서 login 및 인증하기
2. 리뷰
   1. CRUD 기능
   2. 별점 기능
3. 컨텐츠
   1. 가능하다면 외부 API에서 최근 미디어 불러오기 (최근영화, 최근음악, 최근게임)
   2. 리뷰평점의 평균값 나타내기
   3. 작성된 리뷰 모두 보이기
4. 프론트앤드
   1. bootstrap 사용하여 UI 만들기
5. 추가기능
   1. 작성된 리뷰에서 좋아요 표시
   2. AWS 배포하기
   3. 리뷰를 검색하는 기능


| 기능             | Method | URL                  | Request                         | Response                        |
|------------------|--------|----------------------|---------------------------------|----------------------------------|
| 회원가입      | POST   | /users           | email, nickname, password    | 201 Created, 400 Bad Request    |
| 마이페이지 조회 | GET    | /users/{id}      | 없음                            | 200 OK, 404 Not Found           |
| 회원 탈퇴      | DELETE | /users/{id}      | 없음                            | 204 No Content, 404 Not Found   |
| 내가 작성한 리뷰 조회 | GET    | /users/{id}/reviews/{id}      | 없음                      | 200 OK, 404 Not Found           |
| 리뷰 작성 | POST    | /users/{id}/reviews      | 없음                      | 201 Created, 400 Bad Request           |
| 리뷰 수정 | POST    | /users/{id}/reviews/{id}      | 없음                      | 200 OK, 400 Bad Request           |
| 리뷰 삭제 | POST    | /users/{id}/reviews/{id}      | 없음                      | 204 No Content, 404 Not Found           |
| 메인페이지 모든 컨텐츠 조회 | GET    | /contents           | 없음                 | 200 OK, 404 Not Found           |
| 상세 컨텐츠 조회 | GET    | /contents/{id}           | 없음                 | 200 OK, 404 Not Found           |
