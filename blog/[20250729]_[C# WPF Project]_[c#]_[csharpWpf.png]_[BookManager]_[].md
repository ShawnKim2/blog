# WPF 도서 관리 프로그램 - BookManager

---

## 1. 프로젝트 개요

- **이름**: BookManager  
- **기술 스택**: C#, WPF, MVVM, SQLite, Entity Framework Core  
- **개발 목표**: 로컬 데이터베이스를 기반으로 한 도서 CRUD 기능 제공  

---

## 2. 주요 기능

| 기능       | 설명 |
|------------|------|
| **도서 등록** | 책 제목, 저자, ISBN, 출판일 입력 후 등록 가능 |
| **도서 삭제** | 선택한 책 정보를 목록에서 제거 |
| **데이터 저장** | SQLite에 자동 저장 (로컬 파일 `library.db`) |
| **MVVM 패턴 적용** | UI와 로직을 분리하여 유지보수 용이 |

---

## 3. 프로젝트 구조

```
BookManager/
├── Model/
│   └── Book.cs
├── ViewModel/
│   ├── BaseViewModel.cs
│   ├── RelayCommand.cs
│   └── MainViewModel.cs
├── Database/
│   └── LibraryContext.cs
├── MainWindow.xaml
└── MainWindow.xaml.cs
```

---

## 4. 기술 설명

### WPF (Windows Presentation Foundation)

- XAML 기반의 데스크탑 UI 프레임워크  
- `DataBinding` 및 `Command`를 통한 MVVM 아키텍처에 최적화  

### MVVM 패턴

- **Model**: `Book.cs` – 도서 정보를 담는 데이터 클래스  
- **ViewModel**: `MainViewModel.cs` – 데이터 처리 및 명령 로직  
- **View**: `MainWindow.xaml` – UI 레이아웃 및 바인딩 설정  
- `DataContext`를 통해 View와 ViewModel 연결  

### Entity Framework Core + SQLite

- `LibraryContext.cs`는 `DbContext`를 상속하여 SQLite DB 연동  
- `EnsureCreated()`를 통해 앱 실행 시 자동 테이블 생성  
- LINQ 쿼리로 CRUD 처리

---

## 5. 코드

- [코드 링크](https://github.com/ShawnKim2/BookManager)

---

## 6. 실행

- ![
 실행   
](ShawnKim2/blog/img/csharpbookmanager.png)