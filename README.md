# - 유성
마인크래프트 데이터팩 컴파일러 테스트 단계

출처만 표기한다면 자유로운 이용이 가능합니다.
MIT 라이센스를 따릅니다.

# 유성.exe 사용법
 1. 유성.exe파일이 있는 폴더에 확장자가 rkc인 파일을 만드세요.
 2. rkc 파일에서 아래에 설명한 사용법으로 코드를 적으세요.
 3. 코드 작성을 완료하시고 유성.exe를 실행하면 result.mcfunction 파일이 나타납니다.

# 사용법
## 기본 자료형
 - 문자열 ex.) "유성"
 - 숫자 ex.) 42, -41, 4.13
 - 범위 ex.) ..5, 5, 5.., 2..5
 - 리스트 ex.) [1, 2, 3]
 - 딕셔너리 ex.) {"key": "value"}

## 연산자
 - `+`
 - `-`
 - `*`
 - `/`
 - `%`
 - `^ <- 지원 예정`
 - `==`
 - `!=`
 - `>`
 - `<`
 - `>=`
 - `<=`
 - `and`
 - `or`
 - `not`

## 변수 선언
```
let 변수이름 = 값
```
## 변수 값 변경
변수 값을 변경하기 위해서는 변수 선언을 앞에서 해야합니다.
```
변수이름 = 값
```

## if-elif-else
```
let a, b = 10, 20

if a > b:
  print "a가 더 큽니다."
else:
  print "b가 더 큽니다."
end
```
if-else로 연결할 수 있고
if-elif-else로 연결할 수도 있습니다.
마지막에 항상 end를 추가 해야합니다.

```
if a > b :
    print "a가 큽니다"
elif a < b :
    print "b가 큽니다"
else :
    print "같습니다"
end
```

## for
for문은 반복문입니다.
```
for 변수이름 in int1 to int2:
  ...
end
```
마찬가지로 end가 끝에 있어야 합니다.
```
for i in 1 to 5:
  print i
========================
1
2
3
4
5
```

## while
while도 반복문입니다.
```
while true:
  print "계속"
  a = a + 1
  if a > 10:
    break
  end
end
```
while문을 종료시킬 때는 break를 사용해야합니다.
while문도 맨 마지막에 end을 추가해야합니다.

## rkc
rkc는 함수를 선언합니다.
```
rkc 함수이름(매개변수):
  print a, b
end
```
함수 선언할 때도 마지막에 end을 붙여야합니다.
```
rkc add(a,b):
  return a + b
end

print add(1,3)
===================
4
```

## Class
Class는 클래스를 선언합니다.
```
class 클래스이름:
  rkc __init__(self,name):
    self.name = name
  end
end
```
```
class Character:
  rkc __init__(self, name):
    self.name = name
  end

  rkc show(self):
    return self.name
  end
end

let a = Character("유신")
print a.show()
=======================
유신
```

## 리스트
```
let a = []
```
로 선언할 수 있습니다.
```
let list = [1,2]
```
선언과 동시에 값을 지정할 수 있습니다.
### append
리스트는 append를 이용해서 맨 뒤에 값을 넣을 수 있습니다.
```
let list = [1]
list.append(2)
print list
====================
[1, 2]
```
### remove
리스트 값은 삭제 시킬 수도 있습니다.
```
let list = [1, 2]
list.remove(1)
print list
====================
[2]
```
```
let list = [1,2]
list.remove(2)
print list
===================
[1]
```
remove(값)을 적으면 값에 해당하느 인덱스를 찾아 삭제합니다.
### 출력
리스트의 값을 출력할 수 있습니다.
```
let list = [1,2,3]
print list[0]
======================
1
```
## len
len은 길이를 가져옵니다.
```
let a = [1,2,3]
print len(a)
====================
3
```
```
let list = [1,2,3,4,5]

for i in 0 to len(list)-1:
  print list[i]
end
===================
1
2
3
4
5
```
## 딕셔너리
```
let data = ["name": "김치", "age": 25]
print data["name"]
======================
김치
```
## 범위 연산
..5나 5.., 2..5같은 범위 연산자에 연산을 할 수가 있습니다.
```
print ..5 * 2
===================
..10
```
## 입력
input을 이용해서 사용자가 직접 값을 정할 수 있습니다.
```
let name = input("이름 입력: ")
print "안녕하세요, " + name
```
## score
마인크래프트의 스코어보드 관련 코드들입니다.
### score
score는 스코어보드이름을 생성합니다.
```
score a # scoreboard objectives add a dummy
```
### set
스코어보드 이름을 선언했다면 set을 이용해서 값을 지정할 수 있습니다.
```
score set a = 1 # scoreboard players set a a 1
```
### add
스코어보드 이름을 선언했다면 add를 이용해서 현재 스코어보드이름에서 더하기를 할 수 있습니다.
```
score add a = 5 # scoreboard player add a a 5
```
### remove
스코어보드 이름을 선언했다면 remove를 이용해서 스코어보드이름과 해당하는 값을 삭제 할 수 있습니다.
```
score remove = 스코어보드이름
```
### score()
score()를 사용해서 비교 연산이 가능합니다.
```
if score(a) == 20:
  print score(a)
end
```
## tellraw
tellraw함수는 tellraw 명령어를 자동으로 입력해줍니다.
```
tellraw("대사", "선택인자", 스코어보드이름, 범위 연산)
```
```
tellraw("점수를 확인하세요!", "@a", "health", 0..50) # execute as @a if score @a health matches 0..50 run tellraw @s [{"text":"점수를 확인하세요!"}]
```
## random
random이 내장 함수로 존재합니다.
`random.int()` `random.float` 이 존재합니다.
```
random.int(1,100) # 1~100중 무작위
random.float(1,2) # 1.0~2.0중 무작위
```
# 예시
```
score total_score

rkc update_score(points):
    if points > 0 :
        score add total_score = points
        tellraw("점수 +" + str(points) + "획득!", "@a", "total_score", ..1000)
    end
end

for i in 1 to 10 :
    update_score(random.int(1, 100))
end
=================================================================================
scoreboard objectives add total_score dummy
scoreboard players add total_score total_score 100
execute as @a if score total_score total_score matches ..1000 run tellraw @s [{'text':'점수 +100획득!'}]
scoreboard players add total_score total_score 58
execute as @a if score total_score total_score matches ..1000 run tellraw @s [{'text':'점수 +58획득!'}]
scoreboard players add total_score total_score 56
execute as @a if score total_score total_score matches ..1000 run tellraw @s [{'text':'점수 +56획득!'}]
scoreboard players add total_score total_score 53
execute as @a if score total_score total_score matches ..1000 run tellraw @s [{'text':'점수 +53획득!'}]
scoreboard players add total_score total_score 48
execute as @a if score total_score total_score matches ..1000 run tellraw @s [{'text':'점수 +48획득!'}]
scoreboard players add total_score total_score 73
execute as @a if score total_score total_score matches ..1000 run tellraw @s [{'text':'점수 +73획득!'}]
scoreboard players add total_score total_score 57
execute as @a if score total_score total_score matches ..1000 run tellraw @s [{'text':'점수 +57획득!'}]
scoreboard players add total_score total_score 48
execute as @a if score total_score total_score matches ..1000 run tellraw @s [{'text':'점수 +48획득!'}]
scoreboard players add total_score total_score 91
execute as @a if score total_score total_score matches ..1000 run tellraw @s [{'text':'점수 +91획득!'}]
scoreboard players add total_score total_score 1
execute as @a if score total_score total_score matches ..1000 run tellraw @s [{'text':'점수 +1획득!'}]
```
