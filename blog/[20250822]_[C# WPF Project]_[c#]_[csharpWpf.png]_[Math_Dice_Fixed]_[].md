# Math Dice WPF 게임 코드 설명

이번 프로젝트는 **WPF 기반 Math Dice 게임**입니다.
플레이어는 4개의 주사위 숫자를 사용해 목표 숫자를 만들어 승리하는 것이 목표입니다. 최신 버전에서는 **다자리 숫자 사용**, **실시간 입력 검증 강화** 등의 기능을 포함했습니다.

<br/><br/>

프로그래밍에 처음 입문하였을 때, 파이썬으로 제작해본 머드게임 알고리즘을 한 번 C#으로 구현해 보았습니다.

---
# 원래 코드

```python
import random

target = random.randint(1, 12) * random.randint(1, 12)
def roll_dice():
  return random.randint(1, 6)

def play_math_dice(target):
  dice = [roll_dice(), roll_dice(), roll_dice(), roll_dice()]
  

  print('your target number is', target, 'and you got', dice[0] , dice[1] , dice[2] , dice[3],'.')
  answer = str(input('Use the given 4 dice number to derive the correct answer:'))
  answer_num = []
  for num in answer:
    if num.isdigit():
        answer_num.append(num)

  answer_num = ''.join(answer_num)

  digit_list = [int(d) for d in str(answer_num)]
  if dice[0] and dice[1] and dice[2] and dice[3] in digit_list:
    print('you used true number.')
    final_answer = eval(answer)
    if target == final_answer:
      print('you win.')
    else:
      print('you lose.')
  else:
    print('you used false number.')
    print('you lose.')

    
play_math_dice(target)

```


---

# C# WPF 구조로 리메이크

---
## 코드 링크:

- [코드 링크](https://github.com/ShawnKim2/Math_Dice_fixed)
---


## 1. UI 구조 (MainWindow\.xaml)

```xml
<StackPanel>
    <TextBlock x:Name="TargetText" /> <!-- 목표 숫자 표시 -->
    <TextBlock x:Name="DiceText" />   <!-- 주사위 숫자 표시 -->
    <TextBox x:Name="InputBox" />     <!-- 수식 입력 칸 -->
    <TextBlock x:Name="ValidationText" /> <!-- 실시간 입력 검증 -->
    <Button x:Name="SubmitButton" /> <!-- 제출 버튼 -->
    <Button x:Name="RestartButton" /> <!-- 다시 시작 버튼 -->
    <TextBlock x:Name="LogText" />    <!-- 게임 로그 -->
</StackPanel>
```

* 목표 숫자와 주사위를 보여주고,
* 플레이어가 수식을 입력하고 제출,
* 실시간으로 입력 검증 및 로그를 확인할 수 있습니다.

---

## 2. 핵심 변수

```csharp
private int target;        // 목표 숫자
private int[] dice;        // 4개의 주사위 숫자
private int turn = 1;      // 현재 턴
private bool gameOver = false;
private Random rand = new Random();
```

* 목표 숫자 `target`은 1\~12 범위 두 수를 곱하여 생성
* `dice` 배열은 1\~6 범위의 4개의 난수 주사위를 저장
* `gameOver`는 게임 종료 여부 체크

---

## 3. 게임 시작 (StartGame)

```csharp
private void StartGame()
{
    target = rand.Next(1, 13) * rand.Next(1, 13);
    dice = new int[4] { rand.Next(1,7), rand.Next(1,7), rand.Next(1,7), rand.Next(1,7) };
    turn = 1;
    gameOver = false;
    // UI 초기화
}
```

* 목표 숫자와 주사위를 초기화
* 턴, 로그, 입력칸 초기화
* 새로운 게임 시작 시 호출

---

## 4. 실시간 입력 검증 (InputBox\_TextChanged)

```csharp
if (!Regex.IsMatch(expr, @"^[0-9+\-*/()]*$"))
{
    ValidationText.Text = "❌ 숫자와 연산자(+,-,*,/)만 사용 가능합니다!";
    ValidationText.Foreground = Brushes.Red;
    return;
}
```

* 입력 문자열에 숫자와 연산자 외 다른 문자가 들어오면 **즉시 빨간색 경고**
* `"안녕하세요.5"` 같은 입력 시 초록색 표시 안 뜸

```csharp
string[] numbersInExpr = Regex.Matches(expr, @"\d+").Cast<Match>().Select(m => m.Value).ToArray();
bool valid = numbersInExpr.All(n => CanMakeNumberFromDice(n, dice));
```

* 수식에서 사용된 숫자 추출
* `CanMakeNumberFromDice` 함수로 **주사위 숫자를 조합하여 만들 수 있는지** 확인
* 각 숫자가 주사위 숫자로 가능한 경우 초록색 표시

---

## 5. 주사위 조합 검증 (CanMakeNumberFromDice)

```csharp
private bool CanMakeNumberFromDice(string numberStr, int[] diceArray)
{
    int[] diceCopy = (int[])diceArray.Clone();
    foreach (char c in numberStr)
    {
        int digit = c - '0';
        int index = Array.IndexOf(diceCopy, digit);
        if (index == -1) return false;
        diceCopy[index] = -1;
    }
    return true;
}
```

* 다자리 숫자도 허용:

  * 예: `[5,5,2,6]` → `55` 가능
* 각 숫자를 주사위 배열에서 하나씩 사용
* 주사위 숫자를 초과해서 사용하면 실패

---

## 6. 수식 제출 및 승패 판단 (SubmitButton\_Click)

```csharp
var dt = new DataTable();
int result = Convert.ToInt32(dt.Compute(expr, ""));
if (result == target)
{
    AppendLog("✅ 정답! 승리했습니다!");
    EndGame(true);
}
```

* `DataTable.Compute`를 이용해 문자열 수식 계산
* 계산 결과가 목표 숫자와 같으면 승리, 다르면 로그에 오답 표시

---

## 7. 게임 종료 처리 (EndGame)

```csharp
private void EndGame(bool win)
{
    gameOver = true;
    AppendLog("\n=== 게임 종료 ===");
    if (win) AppendLog("🎉 당신이 이겼습니다!");
    else AppendLog("💀 패배했습니다.");
}
```

* 게임 종료 시 입력 및 제출 비활성화
* 로그에 승패 메시지 표시

---

## 8. 주요 개선 포인트

1. **다자리 숫자 허용**

   * `[5,5,2,6]` → `55+6+2` 가능

2. **실시간 입력 검증 강화**

   * 숫자/연산자 외 문자가 포함되면 빨간색 경고
   * 주사위 숫자를 초과 사용하면 빨간색 경고

3. **직관적인 UI와 로그**

   * 턴별 로그, 실시간 피드백, 재시작 버튼

---


## 9. 스크린샷

<p align="center">
  <img src="https://github.com/ShawnKim2/blog/raw/main/img/math_dice1.png" alt="게임 화면"><br/>
  게임 화면
</p>

<p align="center">
  <img src="https://github.com/ShawnKim2/blog/raw/main/img/math_dice2.png" alt="수식 입력"><br/>
  수식 입력
</p>

<p align="center">
  <img src="https://github.com/ShawnKim2/blog/raw/main/img/math_dice3.png" alt="정답, 승리 화면"><br/>
  정답, 승리 화면
</p>

<p align="center">
  <img src="https://github.com/ShawnKim2/blog/raw/main/img/math_dice4.png" alt="숫자 사용 가능 여부"><br/>
  숫자 사용 가능 여부
</p>

<p align="center">
  <img src="https://github.com/ShawnKim2/blog/raw/main/img/math_dice5.png" alt="숫자를 잘못 사용했을 때"><br/>
  숫자를 잘못 사용했을 때
</p>

<p align="center">
  <img src="https://github.com/ShawnKim2/blog/raw/main/img/math_dice6.png" alt="패배 화면"><br/>
  패배 화면
</p>

<p align="center">
  <img src="https://github.com/ShawnKim2/blog/raw/main/img/math_dice7.png" alt="다시 시작"><br/>
  다시 시작
</p>

<p align="center">
  <img src="https://github.com/ShawnKim2/blog/raw/main/img/math_dice8.png" alt="문자 입력 시도"><br/>
  문자 입력 시도
</p>

<p align="center">
  <img src="https://github.com/ShawnKim2/blog/raw/main/img/math_dice9.png" alt="문자 + 수식 입력 시도"><br/>
  문자 + 수식 입력 시도
</p>

