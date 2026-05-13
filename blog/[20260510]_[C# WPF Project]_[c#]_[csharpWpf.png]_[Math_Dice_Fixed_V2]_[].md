# C# WPF 프로젝트 리팩토링 - UI와 MVVM 구조
# ViewModel과 Command 코드 해설

# 기존 프로젝트 링크:

---
## 코드 링크:

- [코드 링크](https://github.com/ShawnKim2/Math_Dice_fixed)
---

# 수정된 프로젝트 링크:

---
## 코드 링크:

- [코드 링크](https://github.com/ShawnKim2/Math_Dice_Fixed_V2)
---

## 왜 MVVM 구조로 변경했을까?

기존 프로젝트는 다음과 같은 구조였다.

* `MainWindow.xaml`

  * 버튼 클릭 이벤트 직접 연결
  * `TextChanged` 이벤트 직접 연결
  * `x:Name` 으로 UI 컨트롤 직접 접근

* `MainWindow.xaml.cs`

  * 게임 로직
  * 상태 관리
  * 입력 검증
  * UI 업데이트
  * 로그 출력

즉, 화면(View)과 로직(Code Behind)이 강하게 결합되어 있었다.

이 방식은 작은 프로젝트에서는 빠르게 개발할 수 있지만, 프로젝트 규모가 커질수록 다음과 같은 문제가 발생한다.

* UI 수정 시 로직도 같이 수정해야 함
* 테스트가 어려움
* 재사용성이 낮음
* 유지보수가 어려움
* 협업 시 충돌 증가

그래서 WPF에서는 보통 MVVM(Model-View-ViewModel) 구조를 사용한다.

---

# MVVM 구조란?

## 1. View

화면(UI)만 담당한다.

예:

* XAML
* 버튼
* 텍스트박스
* 리스트
* 화면 배치

View는 직접 데이터를 처리하지 않는다.

---

## 2. ViewModel

화면과 로직 사이를 연결하는 역할이다.

ViewModel은:

* 화면에 보여줄 데이터 제공
* 버튼 동작 처리
* 상태 관리
* 검증 처리
* 비즈니스 로직 수행

등을 담당한다.

---

## 3. Model

순수 데이터 구조를 의미한다.

예:

* 사용자 정보
* 게임 데이터
* DB 데이터
* DTO

이번 프로젝트에서는 Model이 크지 않기 때문에 별도 분리는 하지 않았다.

---

# MainViewModel 해설

## INotifyPropertyChanged

```csharp
public class MainViewModel : INotifyPropertyChanged
```

MVVM에서 가장 중요한 인터페이스 중 하나이다.

WPF의 Binding 시스템은 속성(Property)이 변경되었는지를 알아야 화면을 자동 갱신할 수 있다.

예를 들어:

```csharp
TargetText = "🎯 목표 숫자: 36";
```

이렇게 값이 변경되면 화면의 TextBlock도 자동으로 변경되어야 한다.

이를 가능하게 만드는 것이 `INotifyPropertyChanged` 이다.

---

# PropertyChanged 이벤트

```csharp
public event PropertyChangedEventHandler? PropertyChanged;
```

속성 값이 변경되었음을 WPF에게 알려주는 이벤트이다.

---

# SetProperty 메서드

```csharp
private bool SetProperty<T>(ref T field, T value, [CallerMemberName] string? propertyName = null)
```

MVVM에서 매우 자주 사용하는 공통 패턴이다.

예:

```csharp
public string TargetText
{
    get => _targetText;
    set => SetProperty(ref _targetText, value);
}
```

이렇게 작성하면:

1. 값 변경
2. PropertyChanged 발생
3. 화면 자동 갱신

이 한 번에 처리된다.

---

# CallerMemberName

```csharp
[CallerMemberName] string? propertyName = null
```

현재 속성 이름을 자동으로 가져온다.

예:

```csharp
TargetText = "Hello";
```

자동으로:

```csharp
PropertyChanged("TargetText")
```

가 호출된다.

즉, 문자열 하드코딩을 줄여준다.

---

# Binding 구조

XAML에서는 다음처럼 작성했다.

```xml
<TextBlock Text="{Binding TargetText}"/>
```

이 의미는:

> 현재 DataContext(ViewModel)의 TargetText 속성과 연결한다.

라는 뜻이다.

즉:

```csharp
TargetText = "🎯 목표 숫자: 24";
```

를 실행하면 화면도 자동 변경된다.

이것이 MVVM의 핵심이다.

---

# Expression 속성의 특징

```csharp
public string Expression
{
    get => _expression;
    set
    {
        if (SetProperty(ref _expression, value))
        {
            ValidateExpression();
            RaiseCanExecuteChanged();
        }
    }
}
```

여기서는 단순 값 변경만 하지 않는다.

값이 바뀔 때:

1. 입력 검증 수행
2. 버튼 활성화 상태 갱신

도 같이 처리한다.

즉:

```xml
UpdateSourceTrigger=PropertyChanged
```

와 결합되어 사용자가 입력할 때마다 실시간 검증이 이루어진다.

---

# Command 패턴이란?

기존 코드에서는:

```xml
<Button Click="SubmitButton_Click"/>
```

처럼 이벤트 기반으로 동작했다.

하지만 MVVM에서는 View와 Code Behind를 분리해야 한다.

그래서 사용하는 것이 `Command` 패턴이다.

---

# ICommand

```csharp
public class RelayCommand : ICommand
```

WPF 버튼은 ICommand를 통해 동작할 수 있다.

즉:

```xml
<Button Command="{Binding SubmitCommand}"/>
```

라고 작성하면:

```csharp
SubmitCommand
```

객체가 실행된다.

---

# RelayCommand 생성자

```csharp
public RelayCommand(Action execute, Func<bool>? canExecute = null)
```

## execute

실제로 실행할 메서드

예:

```csharp
Submit
```

---

## canExecute

버튼 활성화 여부를 결정한다.

예:

```csharp
CanSubmit
```

이 false이면 버튼이 자동 비활성화된다.

---

# SubmitCommand 생성

```csharp
SubmitCommand = new RelayCommand(Submit, CanSubmit);
```

의미:

* 버튼 클릭 시 Submit 실행
* CanSubmit 결과에 따라 버튼 활성화

---

# CanExecute

```csharp
public bool CanExecute(object? parameter)
{
    return _canExecute == null || _canExecute();
}
```

버튼 활성화 가능 여부를 반환한다.

---

# Execute

```csharp
public void Execute(object? parameter)
{
    _execute();
}
```

실제 버튼 클릭 시 실행된다.

---

# RaiseCanExecuteChanged

```csharp
public void RaiseCanExecuteChanged()
```

버튼 활성화 상태를 다시 계산하도록 WPF에 알려준다.

예:

```csharp
RaiseCanExecuteChanged();
```

를 호출하면:

* 버튼 Enable/Disable
* UI 상태

가 자동 갱신된다.

---

# 왜 Code Behind를 비워야 할까?

MVVM의 핵심 목표는:

> UI와 로직의 완전한 분리

이다.

그래서:

## MainWindow.xaml.cs

```csharp
public partial class MainWindow : Window
{
    public MainWindow()
    {
        InitializeComponent();
    }
}
```

정도만 남기는 것이 일반적이다.

---

# MVVM 구조의 장점

## 1. 유지보수성 증가

UI 수정과 로직 수정이 분리된다.

---

## 2. 테스트 용이

ViewModel은 UI 없이도 테스트 가능하다.

---

## 3. 협업에 유리

디자이너:

* XAML 작업

개발자:

* ViewModel 작업

분리가 가능하다.

---

## 4. 재사용성 증가

ViewModel은 다른 View에서도 재사용 가능하다.

---

## 5. 코드 구조가 명확해짐

기능별 역할이 명확하게 분리된다.

---

# 최종 구조

```text
Math_Dice_Fixed_V2
├─ MainWindow.xaml
├─ MainWindow.xaml.cs
├─ ViewModels
│  └─ MainViewModel.cs
└─ Commands
   └─ RelayCommand.cs
```

---

# 마무리

이번 리팩토링의 핵심은:

* 이벤트 기반 구조 → Command 기반 구조
* Code Behind 중심 → ViewModel 중심
* 직접 UI 접근 → Binding 기반 자동 갱신

으로 변경한 것이다.

처음에는 MVVM이 복잡하게 느껴질 수 있지만, 프로젝트 규모가 커질수록 구조적 장점이 매우 커진다.

특히 WPF에서는 MVVM이 사실상 표준 아키텍처에 가깝기 때문에, 실무에서도 매우 자주 사용된다.

이번 프로젝트는 작은 게임 예제이지만:

* 실시간 입력 검증
* Command 패턴
* PropertyChanged
* Binding
* 상태 관리

등 MVVM의 핵심 개념들이 모두 포함된 좋은 연습 기회가 되었다.

# 스크린샷

<p align="center">
  <img src="https://github.com/ShawnKim2/blog/raw/main/img/MathDice리팩토링1.png" alt="게임 화면1"><br/>
  게임 화면1
</p>

<p align="center">
  <img src="https://github.com/ShawnKim2/blog/raw/main/img/MathDice리팩토링2.png" alt="게임 화면2"><br/>
  게임 화면2
</p>

<p align="center">
  <img src="https://github.com/ShawnKim2/blog/raw/main/img/MathDice리팩토링1.png" alt="게임 화면3"><br/>
  게임 화면3
</p>