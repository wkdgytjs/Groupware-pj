
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
    <th>Database</th>
    <th>IDE</th>
    <th>Framework</th>
    <th>Language</th>
  </tr>
  <tr>
    <td>Windows 10</td>
    <td>MySqL</td>
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

## ➰ 게시판 View 영상
![게시판](https://user-images.githubusercontent.com/116870668/234463107-6290e062-10c1-4d1e-87ac-c8c97b2c210e.gif)


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

## ➰ 게시글, 댓글기능 개발 과정에서의 문제점
> 한 사용자가 게시글 상세페이지에서 새로고침이나 수정을 하거나 댓글 작성, 수정, 삭제시 조회수가 올라가는 문제점이 발생하였습니다.
<details>
<summary>BoardController 게시글 상세목록 code</summary>

```Java 
     // 게시글 상세 목록
    @GetMapping("/boardDetail/{boardId}")
    public String boardDetail(@PathVariable("boardId") Long boardId, @AuthenticationPrincipal UserDetails user,
                              Model model) {

        Cookie[] cookies= request.getCookies();

        // 비교하기 위해 새로운 쿠키
        Cookie oldCookie=null;

        //cookies가 null이 아니면 cookie의 이름이 postView인지 확인하고, 맞으면 oldCookie에 이 cookie를 대입
        if(cookies!=null){
            for (Cookie cookie : cookies) {
                if (cookie.getName().equals("postView")) {
                    oldCookie = cookie;
                }
            }
        }

        // 해당 게시판의 번호를 받아 게시글 상세페이지로 넘겨줌
        BoardDto boardDtos = boardService.boardDetailList(boardId);


        if (boardDtos != null) {

            model.addAttribute("boardDtos", boardDtos);

            //만일 oldCookie가 null이 아니고 oldCookie값에 id값이 없을 때
            // (있다면 이미 조회한 게시물로 조회수가 올라가지 않음) 조회수 올리는 메소드 호출
            if (oldCookie!=null) {

                if(!oldCookie.getValue().contains("["+ boardId.toString() +"]")){
                    oldCookie.setValue(oldCookie.getValue() + "_[" + boardId + "]");
                    response.addCookie(oldCookie);
                    //쿠기를 추가 시키고 조회수 증가시킴
                    boardService.upViews(boardId);
                }
            // oldCookie가 null일 경우 postView라는 이름으로 쿠키를 만들고 조회수 올리는 메소드 호출
            }else{
                Cookie newCookie = new Cookie("postView", "[" + boardId + "]");
                newCookie.setMaxAge(-1);
                response.addCookie(newCookie);

                boardService.upViews(boardId);


            // 댓글 작성시 로그인 된 사용자 이름 가져오기
            PoliceDto policeName = policeService.policeEmailSearch(user.getUsername());
            model.addAttribute("policeReplyName", policeName.getPoliceName());

            // 댓글 목록
            List<ReplyDto> replyList = replyService.replyList(boardId);
            model.addAttribute("replyList", replyList);

            return "/board/boardDetail";
        } else {
            return null;
        }
    }  
```  
</details>
<details>
<summary>BoardService 조회수 증가 code</summary> 
  
```Java
    // 게시글 조회시 조회수 1증가
    @Transactional
    public void upViews(Long boardId) {
        boardRepository.updateViews(boardId);
    }
```  
</details>
<details>
<summary>BoardRepository 조회수 증가, 조회수 증가 방지 Native쿼리메소드 code</summary> 
  
```Java
    @Modifying
    @Query(value = "update BoardEntity b set b.views=b.views+1 where b.boardId=:boardId")
    void updateViews(Long boardId);
```  
</details>
 
> 위 코드를 보면 조회수 증가방지를 위해 Cookie를 이용하였지만 아직 Cookie사용에 미숙한 부분이 있어서 <br>
  한 사용자가 하나의 게시글을 조회했을때 쿠키가 생성되면서 나머지 게시글을 조회했을때는 조회수증가가 되지않는 <br>
  문제점이 발생하였습니다.
  
### ❕ 프로젝트 기간내에 생각한 해결방안
 - boardDetail.html에서 key의 value를 true로 설정
  ```
     <a th:href="@{/replyDelete(boardId=${list.boardId},replyId=${list.replyId},key=true)}"
  ```
 - BoardController의 메소드의 인자값으로 @RequestParam() 어노테이션을 넣어 key의 데이터값를 받아 return값에 key값을 같이 보내준다.   
  ```Java
     @PostMapping("/replyWrite")
     public String replyWrite(@ModelAttribute ReplyDto replyDto, Model model,
                             @RequestParam(value = "key", required = false) String key) {

        // 댓글 작성
        replyService.replyWrite(replyDto);
//      System.out.println("id >>>"+replyDto.getBoardId());

        // 댓글 목록 -> 게시글 id(댓글을 단 게시글의 id)의 리스트만 get
        // 댓글을 작성하고 -> 게시글이 존재하는지 확인 -> DTO-> Entity -> 저장
        // 상세목록페이지에 글번호와 댓글리스트를 가지고 같이 보낸다.
        List<ReplyDto> replyList = replyService.replyList(replyDto.getBoardId());
        model.addAttribute("replyList", replyList);

        //게시글 id -> replyDto.getBoardId()/+ 조회수 key
        return "redirect:/boardDetail/" + replyDto.getBoardId() + "/" + key;
    }
  ```  
 - BoardController에 @PathVariable 어노테이션을 이용하여 key값을 받아와, key값에 따라 조회수 카운팅 조건을 다르게 추가
  ```Java
     // 게시글 상세 목록
    @GetMapping("/boardDetail/{boardId}/{key}")
    public String boardDetail(@PathVariable("boardId") Long boardId, @AuthenticationPrincipal UserDetails user,
                              @PathVariable(value = "key", required = false) String key,
                              Model model) {

        // key값이 true이거나 null이 아닌경우 조회수 카운팅 X
        if (key.equals("true") && key != null) {
            boardService.noUpViews(boardId);

            // key값이 true가 아니거나 null인 경우 조회수 카운팅 O
        } else {
            // 게시글 조회수 1증가
            boardService.upViews(boardId);
        }
    }
  ```        
<br> 
       
### ❕ 추후 해결방안
<table>
  <tr>
    <td>댓글 기능 실행 시 다시 로딩하지 않고 자바스크립트를 이용해서 비동기식으로 XML을 이용하여 서버와 통신하는 방식인 ajax를 사용해 추후에 업데이트를 해 볼 생각입니다.
    </td>
  </tr>
</table>
  
  
***
  
🔗Project(team) github Link : [PoliceOfficeGroupware](https://github.com/ckdtls1124/PoliceOfficeGroupware/tree/master)

