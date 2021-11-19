# Chapter 1: Boolean Logic

배경
----
#### 불 대수(Boolean Arithmetic)
참(true)/거짓(false), 1/0, 예/아니오, 켜짐(on)/꺼짐(off) 같은 불(또는 2진수) 값을 다루는 대수학

<br>

#### 불 함수(Boolean Function)
2진수를 입력받아 2진수를 출력하는 함수<br>
컴퓨터는 2진수를 표현하고 처리하는 하드웨어이므로, 불 함수는 컴퓨터 아키텍처에 중요한 역할을 한다.<br>
<br>
아무리 복잡한 불 함수라도 And, Or, Not의 세 가지 불 연산만으로 표현 가능하다.<br>
And, Or, Not 연산을 모두 Nand 연산만으로 만들 수 있다.<br>
따라서 **모든 불 함수는 Nand 연산만으로 표현할 수 있다.**

<br>

#### 2-입력 불 함수
| Function | | |
| :-: | :-: | :-: |
|  | **x** | **0 0 1 1** |
|  | **y** | **0 1 0 1** |
| Constant 0 | 0 | 0 0 0 0 |
| And | x·y | 0 0 0 1 |
| x And Not y | x·y￣ | 0 0 1 0 |
| x | x | 0 0 1 1 |
| Not x And y | x￣·y | 0 1 0 0 |
| y | y | 0 1 0 1 |
| Xor(Exclusive or) | x·y￣+x￣·y | 0 1 1 0 |
| Or | x+y | 0 1 1 1 |
| Nor(Not or) | (x+y)￣￣ | 1 0 0 0 |
| Equivalence | x·y+x￣·y￣ | 1 0 0 1 |
| Not y | y￣ | 1 0 1 0 |
| If y then x | x+y￣ | 1 0 1 1 |
| Not x | x￣ | 1 1 0 0 |
| If x then y | x￣+y | 1 1 0 1 |
| Nand | (x·y)￣￣ | 1 1 1 0 |
| Constant 1 | 1 | 1 1 1 1 |

<br>

#### 게이트 논리
게이트(gate)는 불 함수를 구현한 물리적 장치<br>
n개의 입력 핀과 m개의 출력 핀으로 구성됨

<br>

#### 기본 게이트(Primitive gate)
And, Or, Not

<br>

#### 조합 게이트(Composite gate)
기본 게이트들을 연결하여 조합 게이트를 만든다.

<br>

#### 논리 설계(Logic design)
게이트를 서로 연결해서 더 복잡한 기능을 하는 조합 게이트를 만드는 기술<br>
논리 설계에서 **가장 기본적으로 요구되는 사항**은 어떤 방식으로든 정해진 인터페이스를 따 게이트를 구현하는 것이다.<br>
*(최소 비용 최대 효과)*

<br>

#### 하드웨어 기술 언어(Hardware Description Language, HDL)
하드웨어 설계자들은 HDL 프로그램으로 칩 구조를 작성한다.<br>
HDL을 활용하면, 칩을 설계하고 디버깅하고 최적화하는 일을 전부 수행할 수 있다.<br>

<br>

칩의 HDL 정의는 헤더(header) 부분과 파트(part) 부분으로 구성되어 있다.

<br>

#### 하드웨어 시뮬레이터(Hardware simulator)
HDL 코드의 구문을 분석해서 실행 가능한 표현식으로 변경하고, 주어진 스크립트에 따라 코드를 테스트하는 컴퓨터 프로그램이다.

<br>

명세
---
### Nand 게이트
모든 게이트들의 기초가 되는 게이트<br>
| a | b | Nand(a, b) |
| :-: | :-: | :-: |
| 0 | 0 | 1 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

```
칩 이름: Nand
입력: a, b
출력: out
기능: If a=b=1 then out=0 else out=1.
설명: 이 게이트는 가장 기본이 되는 게이트이므로 따로 구현할 필요가 없다.

```

<br>

### 기본 논리 게이트
Not, And, Or, Xor, Multiplexor, Demultiplexor가 있다.<br>
하지만 이 게이트들도 모두 Nand 게이트만으로 구성이 가능하므로 완전히 기초적인 게이트는 아니다.

#### Not 게이트
단일 입력 Not 게이트는 '컨버터(converter)'라고도 불린다.<br>
입력값을 0에서 1, 1에서 0으로 변환한다.
| a | Not(a) |
| :-: | :-: |
| 0 | 1 |
| 1 | 0 |

```
칩 이름: Not
입력: in
출력: out
기능: If in=0 then out=1 else out=0.
```

<br>

#### And 게이트
입력값이 둘 다 1일 경우 1을, 그 외에는 0을 반환한다.<br>
| a | b | And(a, b) |
| :-: | :-: | :-: |
| 0 | 0 | 0 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |

```
칩 이름: And
입력: a, b
출력: out
기능: If a=b=1 then out=1 else out=0.
```

<br>

#### Or 게이트
입력값 중 적어도 하나가 1일 때 1을, 그 외에는 0을 반환한다.<br>
| a | b | Or(a, b) |
| :-: | :-: | :-: |
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 1 |

```
칩 이름: Or
입력: a, b
출력: out
기능: If a=b=0 then out=0 else out=1.
```

<br>

#### Xor 게이트
'배타적 논리합(exclusive or)'이라고도 불린다.<br>
두 입력값이 다를 경우 1, 그 외에는 0을 반환한다.<br>
| a | b | Xor(a, b) |
| :-: | :-: | :-: |
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

```
칩 이름: Xor
입력: a, b
출력: out
기능: If a!=b then out=1 else out=0.
```

<br>

#### 멀티플렉서(Multiplexor)
3-입력 게이트로, '선택 비트(selection bit)' 입력을 이용해 나머지 두 개의 '데이터 비트(data bit)' 입력 중 하나를 선택한다.<br>
| sel | out |
| :-: | :-: |
| 0 | a |
| 1 | b |

| a | b | sel | out |
| :-: | :-: | :-: | :-: |
| 0 | 0 | 0 | 0 |
| 0 | 1 | 0 | 0 |
| 1 | 0 | 0 | 1 |
| 1 | 1 | 0 | 1 |
| 0 | 0 | 1 | 0 |
| 0 | 1 | 1 | 1 |
| 1 | 0 | 1 | 0 |
| 1 | 1 | 1 | 1 |

```
칩 이름: Mux
입력: a, b, sel
출력: out
기능: If sel=0 then out=a else out=b.
```

<br>

#### 디멀티플렉서(Demultiplexor)
멀티플렉서와 반대의 기능을 한다.<br>
디멀티플렉서는 선택 비트에 따라 두 출력선 중 하나를 선택해 입력 신호를 내보낸다.<br>

| sel | a | b |
| :-: | :-: | :-: |
| 0 | in | 0 |
| 1 | 0 | in |

| in | sel | a | b |
| :-: | :-: | :-: | :-: |
| 0 | 0 | 0 | 0 |
| 0 | 1 | 0 | 0 |
| 1 | 0 | 1 | 0 |
| 1 | 1 | 0 | 1 |

```
칩 이름: DMux
입력: in, sel
출력: a, b
기능: If sel=0 then {a=in, b=0} else {a=0, b=in}.
```

<br>

### 기본 게이트의 멀티비트 버전
컴퓨터 하드웨어는 일반적으로 '버스(bus)'라 불리는 멀티비트 배열에 대해 연산을 수행한다.

#### 멀티비트 Not
n비트 Not 게이트는 n비트 입력 버스의 모든 비트에 대해 Not 연산을 수행한다.

```
칩 이름: Not16
입력: in[16]
출력: out[16]
기능: For i=0..15 out[i]=Not(in[i]).
```

<br>

#### 멀티비트 And
n비트 And 게이트는 두 개의 n비트 입력 버스로 들어오는 모든 n비트 쌍에 대해 And 연산을 수행한다.

```
칩 이름: And16
입력: a[16], b[16]
출력: out[16]
기능: For i=0..15 out[i]=And(a[i], b[i]).
```

<br>

#### 멀티비트 Or
n비트 Or 게이트는 두 개의 n비트 입력 버스로 들어오는 모든 n비트 쌍에 대해 Or 연산을 수행한다.

```
칩 이름: Or16
입력: a[16], b[16]
출력: out[16]
기능: For i=0..15 out[i]=Or(a[i], b[i]).
```

<br>

#### 멀티비트 멀티플렉서
n비트 멀티플렉서는 입력이 n비트라는 점을 제외하면 똑같다. 선택 비트는 여전히 1비트다.

```
칩 이름: Mux16
입력: a[16], b[16], sel
출력: out[16]
기능: If sel=0 then for i=0..15 out[i]=a[i]
     else for i=0..15 out[i]=b[i].
```

<br>

### 기본 게이트의 다입력 버전
2-입력 논리 게이트들은 다입력(multi-way) 게이트로 자연스럽게 일반화할 수 있다.

#### 다입력 Or
n-입력 Or 게이트는 n비트 입력 중 적어도 하나가 1이면 1을 출력하고, 그 외에는 0을 출력한다.

```
칩 이름: Or8Way
입력: in[8]
출력: out
기능: out=Or(in[0], in[1], ..., in[7]).
```

<br>

#### 다입력/멀티비트 멀티플렉서
m-입력 n 비트 멀티플렉서는 m개의 n비트 입력 버스 중에 하나를 골라서 n비트 출력 버스에 출력한다.<br>
선택 입력은 k개의 제어 비트로 되어 있으며, k=log_2 (m)이다.

```
칩 이름: Mux4Way16
입력: a[16], b[16], c[16], d[16], sel[2]
출력: out[16]
기능: If sel=00 then out=a else if sel=01 then out=b
      else if sel=10 then out=c else if sel=11 then out=d
설명: 위에서 언급한 연산들은 모두 16비트다. ex) "out=a"는 "i=0..15에 대해 out[i]=a[i]"라는 뜻
```
```
칩 이름: Mux8Way16
입력: a[16], b[16], c[16], d[16], e[16], f[16], g[16], h[16], sel[3]
출력: out[16]
기능: If sel=000 then out=a else if sel=001 then out=b
      else if sel=010 then out=c ... else if sel=111 then out=h
설명: 위에서 언급한 연산들은 모두 16비트다. ex) "out=a"는 "i=0..15에 대해 out[i]=a[i]"라는 뜻
```

<br>

#### 다입력/멀티비트 디멀티플렉서
m-입력 n 비트 디멀티플렉서는 n비트 입력을 하나 받아 m개의 n비트 출력 중 하나로 내보낸다.<br>
선택 입력은 k개의 제어 비트로 되어 있으며, k=log_2 (m)이다.

```
칩 이름: DMux4Way
입력: in, sel[2]
출력: a, b, c, d
기능: If sel=00 then      {a=in, b=c=d=0}
      else if sel=01 then {b=in, a=c=d=0}
      else if sel=10 then {c=in, a=b=d=0}
      else if sel=11 then {d=in, a=b=c=0}.
```
```
칩 이름: DMux8Way
입력: in, sel[3]
출력: a, b, c, d, e, f, g, h
기능: If sel=000 then      {a=in, b=c=d=e=f=g=h=0}
      else if sel=001 then {b=in, a=c=d=e=f=g=h=0}
      else if sel=010 ...
      ...
      else if sel=111 then {h=in, a=b=c=d=e=f=g=0}.
```

<br>
