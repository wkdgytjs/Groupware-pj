# Police office + Grouware Project 🚔
> 2023.03.14 ~ 2023.04.06까지 진행한 그룹웨어 기본 연동 기능 구현 프로젝트입니다.
🔗Project Link : [PoliceOfficeGroupware](https://github.com/ckdtls1124/PoliceOfficeGroupware/tree/master_upload)
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

## ➰프로젝트 구성(Spring MVC Model2)
![design](https://user-images.githubusercontent.com/116870668/233907336-53c5b845-5826-420e-b0ec-0279f3a232e5.jpg)

<br>

## ➰개발 관련 문서
<details>
<summary> ERD </summary>

![DB design_2](https://user-images.githubusercontent.com/116870668/233940813-2613f5dc-58da-4786-81c3-f737ff3930f9.png)

</details>

<br>

## ➰사용한 기술 및 배포 환경
<table>
  <tr>
    <th>OS</th>
    <th>Database</th>
    <th>IDE</th>
    <th>Framework</th>
    <th>Language</th>
    <th>AWS</th>
  </tr>
  <tr>
    <td>Windows 10</td>
    <td>MySqL</td>
    <td>IntelliJ, Visual Studio Code</td>
    <td>Spring Boot</td>
    <td>Java, HTML, CSS, Javascript</td>
    <td>CodeDeploy, IAM, EC2, S3, RDS</td>
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

<br>



