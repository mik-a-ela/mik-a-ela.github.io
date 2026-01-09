---
title: "Project #01: 지능형 숫자 맞추기 게임"
description: 컴퓨터가 생각한 비밀 숫자를 맞혀라!
date: 2026-01-10
tags: [Python, 게임, 기초]
---

# Project #01: 지능형 숫자 맞추기 게임

**Status:** ✅ SUCCESS | **Category:** Python 기초 | **Difficulty:** ★☆☆☆☆

---

## 📝 미션

컴퓨터가 생각한 비밀 숫자를 맞혀라!

컴퓨터는 친절하게 힌트(UP/DOWN)를 주고, 당신이 몇 번 만에 맞혔는지까지 기억할 것이다.  
**얼마만에 맞힐 수 있을까?**

---

## 💡 핵심 규칙

| 규칙 | 설명 | 구현 |
|------|------|------|
| **범위 밖은 무효** | 1~100 사이가 아닌 숫자를 말하면, 기회를 차감하지 않고 "다시 말해달라"고 정중히 부탁하기 | `continue` |
| **기억력 기르기** | 맞힐 때까지 횟수를 하나씩 세어서, 마지막에 "O번 만에 맞혔어!"라고 알려주기 | `count += 1` |
| **에러 방패** | 숫자가 아닌 글자를 입력해도 프로그램이 갑자기 꺼지지 않게 방패막 설치하기 | `try-except` |

---

## 🖥️ 코드

```python
import random

# 1부터 100까지 랜덤 숫자 생성
secret_number = random.randint(1, 100)
count = 0

print("🎮 숫자 맞추기 게임에 오신 것을 환영합니다!")

while True:
    try:
        guess = int(input("1부터 100까지의 정수 중 하나를 적어주세요: "))
        
        # 범위 체크
        if guess < 1 or guess > 100:
            print("❌ 1~100 사이 숫자만 입력해주세요!")
            continue
        
        count += 1
        
        if guess < secret_number:
            print("⬆️ 너무 낮아요! UP!")
        elif guess > secret_number:
            print("⬇️ 너무 높아요! DOWN!")
        else:
            print(f"🎉 정답이에요! {count}번 만에 맞혔어요!")
            break
            
    except ValueError:
        print("⚠️ 정수가 입력되지 않았습니다. 숫자만 넣어주세요!")
```

---

## 🎯 실행 결과

```
🎮 숫자 맞추기 게임에 오신 것을 환영합니다!
1부터 100까지의 정수 중 하나를 적어주세요: 50
⬆️ 너무 낮아요! UP!
1부터 100까지의 정수 중 하나를 적어주세요: 75
⬆️ 너무 낮아요! UP!
1부터 100까지의 정수 중 하나를 적어주세요: 79
🎉 정답이에요! 3번 만에 맞혔어요!
```

---

## 📚 배운 점

- `random.randint()` — 랜덤 숫자 생성
- `try-except` — 잘못된 입력 처리 (에러 방패)
- `continue` — 조건 불충족시 다시 시도
- `while True` + `break` — 게임 루프 구현
