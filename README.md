# LingoHub

**LingoHub**는 AI와 함께하는 영어 공부 커뮤니티입니다.

AI는 물론 영어 공부를 하는 사람들과 소통하며 학습할 수 있습니다. 

- Gemini API를 이용해 사진으로 영어 문제 관련 질문을 할 수 있습니다.
- Gemini의 답변을 저장을 하고 싶다면 저장을 하고 복습에 사용할 수 있습니다.
- Gemini의 답변에서 궁

## Outline

### 개발환경

- 프론트엔드: Flutter
- 백엔드-서버: Django
- DB: MySql
- Cloud: AWS
- SDK Login: Kakao

### Team

안세혁

[shyukahn - Overview](https://github.com/shyukahn)

정민규

[alsrb595 - Overview](https://github.com/alsrb595)

## LingoHub 소개


### 1. 로그인 화면

![로그인 화면](images/login_page.png | width=100)

**주요기능**

- 카카오톡을 이용한 간편한 소셜 로그인
- 로그인이 되어있는 경우 바로 메인 화면으로 이동

**기술설명**

- 로그인 시 서버에 유저 정보를 전송하고 새로 가입하는 유저는 유저 정보 테이블에 추가됩니다.
- 카카오 SDK를 이용하여 유저의 닉네임, 프로필 사진을 받아옵니다.

### 2. 메인 커뮤니티 탭

![메인 커뮤니티 화면](images/tab1_community_page.png)    ![글 작성](images/tab1_add_post.gif)    ![댓글 작성](images/tab1_add_comment.gif)    ![게시물 삭제](images/tab1_delete_post.gif)

**주요 기능**

- 최근 게시글을 모아 볼 수 있습니다.
- 게시글을 선택하면 작성자 프로필, 댓글 등의 정보를 확인할 수 있습니다.
- 게시글에 추가로 댓글을 작성할 수 있습니다.
- 저장하고 싶은 게시글은 스크랩할 수 있습니다.

**기술 설명**

- 서버에 GET 요청을 보내 DB의 모든 게시글의 요약 정보를 특정 `serializer`를 통해 생성 후  최신순으로 정렬하여 클라이언트로 반환 → `ListView`로 표현합니다.
- 게시글을 클릭하면 서버에 GET 요청을 보내 해당 게시글의 상세 정보를 받아옵니다.
- 댓글을 입력하고 버튼 터치 → 서버에 댓글관련 정보를 서버에 POST 요청으로 comment 테이블에 저장
- 스크랩 기능:
    
    게시글 상세 페이지에 별모양 터치 → POST 요청으로 scrabpost 테이블에 저장 → 다시 별표를 누르면 색이 없어짐 → DELETE 요청으로 scrabpost 테이블에서 삭제
    
- 글 삭제 기능:
    
    게시글 상세페이지에서 별 옆의 아이콘 버튼 터치 → 게시글 삭제 메세지 → DELETE 요청으로 post 테이블에서 삭제 
    
- 글 추가 기능:
    
     `FloatingActionButton`을 누르면 게시글 추가 페이지로 이동 → 제목, 본문 입력 후 등록 버튼 터치 → 게시글 관련 정보 POST로 post테이블에 저장 
    

### 3. AI 질문 페이지

![Gemini 질문](images/tab2_gemini_responses.png)    ![Gemini 답변](images/tab2_get_gemini_response.gif)    ![Gemini 답변 공유](images/tab2_share_gemini_response.gif)

- AI에게 사진으로 질문:
    
     `FloatingActionButton` 을 눌러 갤러리의 사진 또는 촬영을 통한 영어 문제 질문 → Gemini의 답변 생성
    
- 답변 저장 기능:
    
    답변 생성 후 추가 버튼 터치 → user_question 테이블에 저장 → AI 질문 탭에 저장한 질문 리스트에 추가됨
    
- 커뮤니티로 질문:
    
    답변 생성 후 공유 버튼 터치 → 바로 게시글 작성 페이지로 넘어감 → 본문 내용에 자동으로 AI의 답변이 추가 됨 → 궁금한점 추가하며 게시글 등록 → post 테이블에 저장
    

### 4. 마이페이지

![마이페이지](images/tab3_mypage.png)    ![스크랩](images/tab3_scrap.gif)

- 회원정보
- 스크랩한 게시글 버튼 터치 → 스크랩한 게시글들의 리스트 → 터치하면 그 게시물의 상세페이지로 이동

### LingoHub apk

[lingoHub.apk](https://drive.google.com/file/d/1qz-DeIaiIwX0pTb7HqmJC-NbHeKcHGPN/view?usp=sharing)
