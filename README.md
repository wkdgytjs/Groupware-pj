
# Police office + Grouware Project 🚔
> 2023.03.14 ~ 2023.04.06까지 진행한 그룹웨어 기본 연동 기능 구현 프로젝트입니다.

## ❕ Description ❕
<table>
  <tr>
    <td>
지구대에서 쓰일 만한 관리자 페이지를 가정하여 제작한 사이트
    </td>
  </tr>
</table>

![MainIndex_2](https://user-images.githubusercontent.com/116870668/233940183-dcf7cc55-51af-4d64-98f3-b24696c19a9f.jpg)

<br>

## ➰기획 배경 및 해결하고자 하는 문제
<table>
  <tr>
    <td>
관리자 페이지는 원활한 업무 처리를 위한 페이지이고, 일반적인 게시판과 달리 더욱 많은 기능을 제어하고 사용할 수 있는 권한을 부여할 수 있습니다.
또, 경찰의 업무는 사건 사고를 중심으로 업무가 진행되므로 사건 사고에 중점을 두고 제작하였습니다.
    </td>
  </tr>
</table>

<br>


## ➰개발 관련 문서
<details>
<summary>비즈니스 로직</summary>
  
![BusinessLogic](https://user-images.githubusercontent.com/116870668/234459286-41b37829-c274-42ec-a412-015c749e4fe1.png)

</details>
<details>
  
<summary>ERD</summary>
  
![DB design_2](https://user-images.githubusercontent.com/116870668/233940813-2613f5dc-58da-4786-81c3-f737ff3930f9.png)

</details>

<br>

## ➰사용한 기술 및 배포 환경
<table>
  <tr>
    <th>OS</th>
    <th>Infra & DB</th>
    <th>IDE</th>
    <th>Framework</th>
    <th>Language</th>
  </tr>
  <tr>
    <td>Windows 10</td>
    <td>MySqL, AWS</td>
    <td>IntelliJ, Visual Studio Code</td>
    <td>Spring Boot</td>
    <td>Java, HTML, CSS, Javascript</td>
  </tr>
</table>

<br>

## ➰Team (담당한 업무)
<details>
<summary> 강창신 </summary>

1. 결재문서 CRUD
2. 근태 기능
3. naver-API
</details>
<details>
<summary> 김득주 </summary>

1. 로그인&Spring Security
2. 아이디/비밀번호 찾기
</details>
<details>
<summary> 이지창 </summary>

1. 회원CRUD
2. 부서CRUD
3. FullCalendar-API
4. AWS EC2 배포
</details>
<details>
<summary> 장효선 </summary>

1. 게시판CRUD
2. 댓글CRUD
3. 각 페이지 design frame(Html,CSS) 제작
</details>
<details>
<summary> 허인경 </summary>
  
1. 사건CRU
2. left-Menubar 제작
3. KakaoMap-API
</details>


***
## 📋 게시판 기능

<table>
  <tr>
    <td>
게시판은 공지게시판으로 지정하여 관리자 권한이 있는 사용자만 등록, 수정, 삭제 권한을 부여하여 처리 하였습니다.
    </td>
  </tr>
</table>

<br>

## ➰ 게시판 View 영상
![게시판](https://user-images.githubusercontent.com/116870668/234463107-6290e062-10c1-4d1e-87ac-c8c97b2c210e.gif)

<br>

### 디렉토리 구성 및 ERD
<details>
<summary>디렉토리 구성</summary>
  
![board](https://user-images.githubusercontent.com/116870668/234480544-623e77f3-2864-4a72-a0ce-c9d6751801df.jpg)

</details>
<details>
  
<summary>ERD</summary>
  
![boardDB](https://user-images.githubusercontent.com/116870668/234481357-25114d5d-a33a-47fe-a064-0cdccb5cd90c.jpg)
  
> 사용자 한명이 여러 게시글을 작성할 수 있으므로 police_officer 테이블은 board테이블과 1:N 관계 설정
</details>

***
## ✏️ 댓글 기능

<table>
  <tr>
    <td>
댓글은 게시글 상세 페이지에서 작성가능하며 본인의 댓글만 수정, 삭제 권한을 부여하여 처리하였습니다.
    </td>
  </tr>
</table>

<br>

## ➰ 댓글 View 영상
![댓글](https://user-images.githubusercontent.com/116870668/234489338-dde939bc-fa1a-4fbc-a3c2-d58770c2eb2a.gif)

<br>

### 디렉토리 구성 및 ERD
<details>
<summary>디렉토리 구성</summary>
  
![reply](https://user-images.githubusercontent.com/116870668/234490549-484c08b3-5cfa-4261-9301-900ce0c00c18.jpg)
  
> 댓글은 게시글 상세페이지에서 작성할 수 있으므로 View단 파일을 별도로 생성하지 않고, boardDetail.html에 처리해줬습니다.
</details>
<details>
  
<summary>ERD</summary>
  
![replyDB](https://user-images.githubusercontent.com/116870668/234490541-27b061cd-7e77-4848-9e64-17e7b4cb91b0.jpg)
  
> 사용자 한명이 게시글 한 곳에 댓글을 여러개 작성할 수 있으므로 board_reply 테이블은 police_officer, board 테이블과 각각 N:1 관계 설정
</details>


🔗Project(team) github Link : [PoliceOfficeGroupware](https://github.com/ckdtls1124/PoliceOfficeGroupware/tree/master_upload)

