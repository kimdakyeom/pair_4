# Django 페어프로그래밍 04
## 결과물✨
- 클릭

[영화 리뷰 사이트](https://limitless-plains-68775.herokuapp.com/)
- 회원가입 & 로그인

![ezgif com-gif-maker](https://user-images.githubusercontent.com/74820869/198831844-9782e75c-50fa-4853-a287-bfbc41cf4067.gif)

- 리뷰 글 생성 & 수정 & 삭제

![ezgif com-gif-maker (1)](https://user-images.githubusercontent.com/74820869/198831934-82847e2d-e858-4845-825f-97cc6517a065.gif)

- 영화 카테고리 기능

![ezgif com-gif-maker (2)](https://user-images.githubusercontent.com/74820869/198832127-54606bf2-91d3-4817-98e7-34f80d2979b8.gif)

- 댓글 & 좋아요 기능

![ezgif com-gif-maker (4)](https://user-images.githubusercontent.com/74820869/198832265-81e466c5-d041-46e8-bb9a-17015f8efb76.gif)

- 프로필 팔로우 기능

![ezgif com-gif-maker (3)](https://user-images.githubusercontent.com/74820869/198832213-dde17a81-9762-4f12-a2a6-d732c6f2af52.gif)

## 목표📚
페어 프로그래밍을 통한 영화 리뷰 커뮤니티 서비스를 개발합니다.
- **CRUD** 구현(구현 방법 제한 없음)
- **Staticfiles** 활용 정적 파일(이미지, CSS, JS) 다루기
- Django **Auth** 활용 회원 관리(회원 가입 / 회원 조회 / 로그인 / 로그아웃)
- Media 활용 동적 파일 다루기
- 모델간 **1 : N / M : N 관계** 매핑
- Heroku를 사용하여 홈페이지 배포

## 요구 사항📄
### 모델 Model

- 모델 이름 : User
    
    Django **AbstractUser** 모델을 상속 받고, 필드를 직접 정의하세요.
    
- 모델 이름 : Review
    
    모델의 필드를 직접 정의하세요.
    

- 모델 이름 : Comment
    
    모델의 필드를 직접 정의하세요.
    

### **폼 Form**

회원 가입

- Django 내장 회원 가입 폼 UserCreationForm을 상속 받아서 CustomUserCreationForm 생성
- 출력할 필드를 직접 정의합니다.

로그인

- Django 내장 로그인 폼 AuthenticationForm 활용

### 기능 View

**리뷰 reviews**

데이터 목록 조회

- `GET` http://127.0.0.1:8000/reviews/
- 국내영화 / 해외영화에 해당하는 게시물만 출력됩니다.

데이터 정보 조회

- `GET` http://127.0.0.1:8000/reviews/<int:review_pk>/

데이터 생성 

- `POST` http://127.0.0.1:8000/reviews/create/
- 로그인한 유저만 데이터 생성이 가능합니다.

데이터 수정

- `POST` http://127.0.0.1:8000/reviews/<int:review_pk>/update/
- 해당 리뷰 작성자만 수정할 수 있습니다.

데이터 삭제

- `POST` http://127.0.0.1:8000/reviews/<int:review_pk>/delete/
- 해당 리뷰 작성자만 삭제할 수 있습니다.

리뷰 좋아요 / 좋아요 취소

- `POST` http://127.0.0.1:8000/reviews/<int:review_pk>/like/
- 로그인한 유저만 좋아요 기능을 사용할 수 있습니다.

**댓글 comments**

리뷰의 댓글 목록 조회

- `GET` http://127.0.0.1:8000/reviews/<int:review_pk>/
- 해당 게시글의 댓글 목록 조회

댓글 생성

- `POST` http://127.0.0.1:8000/reviews/<int:review_pk>/comments/create/
- 로그인한 유저만 댓글 생성이 가능합니다.

**회원 관리 accounts**

회원 가입

- `POST` http://127.0.0.1:8000/accounts/signup/

회원 목록 조회

- `GET` http://127.0.0.1:8000/accounts/

회원 정보 조회

- `GET` http://127.0.0.1:8000/accounts/<int:user_pk>/

로그인

- `POST` http://127.0.0.1:8000/accounts/login/

로그아웃

- `POST` http://127.0.0.1:8000/accounts/logout/

팔로우

- `POST` http://127.0.0.1:8000/accounts/<int:user_pk>/follow/
- 로그인한 유저만 팔로우 기능을 사용할 수 있습니다.
- 자기 자신은 팔로우 할 수 없습니다.

### 화면 Template

**네비게이션바, Bootstrap `<nav>`**

- 서비스 로고
- 리뷰 목록 페이지 이동 버튼
- 리뷰 작성 페이지 이동 버튼
- 로그인 상태에 따라 다른 화면을 출력합니다.
    1. 로그인 상태
        - 로그인한 사용자의 username
        - 로그아웃 버튼
    2. 비 로그인 상태
        - 로그인 페이지 이동 버튼
        - 회원 가입 페이지 이동 버튼

**메인 페이지**

- `GET` http://127.0.0.1:8000/
- 자유 디자인

**목록 페이지** 

- `GET` http://127.0.0.1:8000/reviews/

**리뷰 정보 페이지**

- `GET` http://127.0.0.1:8000/reviews/<int:review_pk>/
- 해당 리뷰 정보 출력
- 댓글 작성 폼
- 해당 리뷰에 작성된 댓글 목록
    - 각 댓글에는 삭제 버튼이 있습니다. 단, 댓글 작성자만 삭제를 할 수 있습니다.
- 좋아요 버튼
    - 해당 리뷰의 좋아요 개수를 함께 출력합니다.
    - 로그인한 유저는 리뷰에 좋아요를 남길 수 있습니다.

**리뷰 작성 페이지**

- `GET` http://127.0.0.1:8000/reviews/create/
- 리뷰 작성 폼

**리뷰 수정 페이지**

- `GET` http://127.0.0.1:8000/reviews/<int:review_pk>/update/
- 리뷰 수정 폼

회원 가입 페이지

- `GET` http://127.0.0.1:8000/accounts/signup/
- 회원 가입 폼

회원 조회 페이지(프로필 페이지)

- `GET` http://127.0.0.1:8000/accounts/<int:user_pk>/
- 회원이 작성한 게시글 목록 출력

로그인 페이지

- `GET` http://127.0.0.1:8000/accounts/login/
- 로그인 폼
- 회원 가입 페이지 이동 버튼

팔로우 버튼

- 로그인한 유저는 해당 유저를 팔로우 할 수 있습니다.
- 단, 자기 자신은 팔로우 할 수 없습니다.

## 후기💪🏻
- 이번주에 배운 DB의 N:M 관계와 비동기 처리 내용이 어려워서 해메고 있었는데 페어 프로그래밍으로 해당 내용을 활용하며 프로젝트를 진행하니 이해도가 높아졌다.
- AJAX 통신이 어떤식으로 진행되는지에 대해 더 생각해 볼 수 있는 시간이었다.
- Haroku를 이용해 처음 사이트를 배포해보았고, 배포를 하던 도중 많은 에러를 만났지만 이를 해결하면서 문제 해결력을 기를 수 있었다.
- Haroku로만 배포를 진행하니 정적 이미지는 배포가 불가능하여서 추후에 S3나 AWS도 활용하여 배포를 진행하면 좋을 것 같다.