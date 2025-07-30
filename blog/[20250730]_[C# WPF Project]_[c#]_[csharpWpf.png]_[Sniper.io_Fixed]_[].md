# Sniper.io WPF

간단한 WPF 기반 턴제 전략 게임입니다.  
수비수로서 저격수를 막아내고 승리하세요!

---

## 1. 게임 룰
- 저격수: 저격과 폭격 둘 중 하나의 행동을 할 수 있음.
- 저격: 수비수를 공격. 우선도 +1, 저격은 7번만 사용할 수 있음.
- 폭격: 수비수를 공격. 수비수의 수비를 뚫고 공격. 우선도 -4

<br/>

- 수비수: 수비와 반격 둘 중 하나의 행동을 할 수 있음.
- 수비: 저격수의 저격을 막음. 우선도 +2
- 반격: 저격수를 공격. 우선도 0

---

## 2. 주요 기능
- 수비 / 반격 전략 선택
- 적 행동 랜덤화 (저격 / 폭격)
- 턴 기반 우선순위 로직
- 게임 상태 시각화 (체력바, 로그, 텍스트 상태)

---

## 3. 기술 스택
- C#
- WPF (XAML)
- MV 구조 기반 단순 아키텍처

---

## 4. 코드

- [코드 링크](https://github.com/ShawnKim2/Sniper_io_fixed)

---

## 5. 실행 방법
1. Visual Studio 2022 이상에서 `.sln` 열기
2. 실행 (`F5`)

---

## 6. 스크린샷

<p align="center">
  <img src="https://github.com/ShawnKim2/blog/raw/main/img/csharpsniper1.png" alt="게임 화면"><br/>
  게임 화면
</p>

<p align="center">
  <img src="https://github.com/ShawnKim2/blog/raw/main/img/csharpsniper2.png" alt="1턴 경과"><br/>
  1턴 경과
</p>

<p align="center">
  <img src="https://github.com/ShawnKim2/blog/raw/main/img/csharpsniper3.png" alt="2턴 경과, 반격 성공"><br/>
  2턴 경과, 반격 성공
</p>

<p align="center">
  <img src="https://github.com/ShawnKim2/blog/raw/main/img/csharpsniper4.png" alt="승리 화면"><br/>
  승리 화면
</p>




