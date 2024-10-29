# 📱 24-25 App Assignment 

## 📝 과제 수행 관련
3차시 과제는 hw01, hw02 문제 2개입니다.
git fork을 이용해 과제 수행하시면 됩니다.
VS Code를 사용하시거나, 아직 설치가 되어있지 않으신 분들은 DartPad를 사용하시면 됩니다.

## ‼️ 과제 제출 관련
과제에 대한 코드를 작성하시고, Pull Request(PR)를 작성해주시면 됩니다.
PR 제목은 24-25-APP-Assignment-03 본인이름으로 통일하겠습니다.
PR 작성하실 때, 궁금한 점이나 어려웠던 점 등을 적어주세요.
과제 제출 마감 기한은 11월 일 23:59까지입니다.
## 👩‍💻 문제 목록

### 1️⃣ 비동기 도서 관리 시스템

> 비동기 도서 관리 시스템을 개선하여 Null Safety를 적용하고, 책이 존재하지 않은 경우 화면에 null을 알릴 수 있는 정보를 화면에 출력
>
- Book 클래스 : 도서에 대한 정보를 가지고 있는 클래스
    - 속성  (아래 3개는 필수적으로 구현해야하는 속성이고, 추가적으로 구현해도 됨)
        - `title` : 책의 제목을 나타내는 속성 (String)
        - `author` : 저자 이름을 나타내는 속성 (String)
        - `isAvaliable` : 책의 대출 가능 여부를 나타내는 속성(boolean ) ** 기본 값은 true
    - 메서드
        - borrow() :
            - 책을 대출하는 비동기 메서드로 대출 가능 여부 확인 가능  대출 후
            - `isAvailable`을 `false`로 설정
        - returnBook() : 책을 반납하는 비동기 메서드로 1초 지연 후, `isAvaliable`을 `true`로 설정하고 “반납되었습니다.” 메세지 출력
        
- Library 클래스 : 도서 목록을 저장하고 관리하는 클래스
    - 속성
        - `books` : 도서 목록을 저장하는 리스트
    - 메서드
        - `addBook(Book book)` : `Book`을 인자로 받아, 새로운 도서 목록을 추가하며, 1초 지연 후 책의 제목과 저자를 추가하는 메세지 출력
        - `searchByTitle(String? title)` : 제목을 기준으로 책을 검색하는 비동기 메서드로, 1초 지연 후 해당 제목의 책이 존재하면 책의 제목과 저자를 출력, `nulll`이거나 존재하지 않으면 “책을 찾을 수 없습니다”라는 메세지 출력
            
            ** title이 null인 경우 “제목이 null입니다”메세지 출력
            
- main 클래스
    - Book  객체와 Library
    - 객체를 생성하여, 책을 추가하고, 대출 중인지 확인 가능함.
    - null 값을 가진 제목으로 검색을 할 수 있음

---

### 2️⃣ 교통수단 관리 시스템

> 교통수단 관리 시스템, `Vehicle` 클래스를 상속받아 3개 이상의 교통수단 구현
>
- `Vehicle` 클래스
    - 추상 클래스로, 교통 수단에 필요한 필수적인 이동방식이 있는 클래스
    - 속성
        - `name` (String) : 교통 수단의 이름을 가지고 있음.
        - `speed`(int) : 해당 교통 수단의 속력
    - 메소드
        - `move()`  : 교통 수단에 따라 고유의 방식으로 다르게 구현하는 추상 메서드
        - `info()` : 교통 수단의 정보를 알려주는 일반 메서드
            - ex ) 출력값 :  `자동차`가 시속 `speed`km/h의 속도로 이동합니다.
- `Transportation` 클래스
    - `Vehicle` 클래스를 상속받은 교통수단 클래스
    - 각 클래스에서 `move()` 메서드를 오버라이드 하여 구현
    - 기존에 있던 `Car클래스`에는 추가적으로 `stop()` 메소드 구현 : `stop()`이 실행되면 speed값이 0으로 초기화 됨.
- `main()`
    - Vehicle 타입을 가지는 List vehicles를 생성하여 여러 종류의 교통 수단 객체를 추가
    - `for문`을 이용해 `vehicles` 리스트에 있는 모든 교통 수단의 `info()`와 `move()` 메서드를 호출