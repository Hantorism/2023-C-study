# 3회차 실습

## Practice 1: 사칙연산

<details>
<summary>[Solution]</summary>

<details>
<summary>if</summary>

```C
#include <stdio.h>

int main() {
    int operand1, operand2;
    char operator;

    printf("수식 입력: ");
    scanf("%d %c %d", &operand1, &operator, &operand2);

    if (operator == '+') {
        printf("결과: %d\n", operand1 + operand2);
    }
    else if (operator == '-') {
        printf("결과: %d\n", operand1 - operand2);
    }
    else if (operator == '*') {
        printf("결과: %d\n", operand1 * operand2);
    }
    else if (operator == '/') {
        printf("결과: %d\n", operand1 / operand2);
    }
    else {
        printf("올바른 연산자를 입력해주세요\n");
    }

    return 0;

}
```

</details>

<details>
<summary>switch</summary>

```C
#include <stdio.h>

int main() {
    int operand1, operand2;
    char operator;

    printf("수식 입력: ");
    scanf("%d %c %d", &operand1, &operator, &operand2);

    switch (operator) {
        case '+':
            printf("결과: %d\n", operand1 + operand2); break;
        case '-':
            printf("결과: %d\n", operand1 - operand2); break;
        case '*':
            printf("결과: %d\n", operand1 * operand2); break;
        case '/':
            printf("결과: %d\n", operand1 / operand2); break;
        default:
            printf("올바른 연산자를 입력해주세요\n");
    }

    return 0;
}
```

</details>

</details>

## Practice 2: 당신의 학점은?

<details>
<summary>[Solution]</summary>

<details>
<summary>if</summary>

```C
#include <stdio.h>

int main() {
    int score;

    scanf("%d", &score);

    if (score >= 90) {
        printf("학점: A\n");
    }
    else if (score >= 80) {
        printf("학점: B\n");
    }
    else if (score >= 70) {
        printf("학점: C\n");
    }
    else if (score >= 60) {
        printf("학점: D\n");
    }
    else {
        printf("학점: F\n");
    }

    return 0;
}
```

</details>

<details>
<summary>switch</summary>

```C
#include <stdio.h>

int main() {
    int score;

    scanf("%d", &score);

    switch (score / 10) {
        case 10:
        case 9:
            printf("학점: A\n"); break;
        case 8:
            printf("학점: B\n"); break;
        case 7:
            printf("학점: C\n"); break;
        case 6:
            printf("학점: D\n"); break;
        default:
            printf("학점: F\n");
    }

    return 0;
}
```

</details>

</details>

## Practice 3: 최댓값 구하기

<details>
<summary>[Solution]</summary>

<details>
<summary>nested if</summary>

```C
#include <stdio.h>

int main() {
    int num1, num2, num3;

    printf("세 정수: ");
    scanf("%d %d %d", &num1, &num2, &num3);

    if (num1 > num2) {
        if (num1 > num3) {
            printf("가장 큰 수: %d\n", num1);
        }
        else {
            printf("가장 큰 수: %d\n", num3);
        }
    }
    else {
        if (num2 > num3) {
            printf("가장 큰 수: %d\n", num2);
        } else {
            printf("가장 큰 수: %d\n", num3);
        }
    }

    return 0;
}
```

</details>

<details>
<summary>삼항연산자</summary>

```C
#include <stdio.h>

int main() {
    int num1, num2, num3;
    int max;

    printf("세 정수: ");
    scanf("%d %d %d", &num1, &num2, &num3);

    max = (num1 > num2) ? num1 : num2;
    max = (max > num3) ? max : num3;

    printf("가장 큰 수: %d\n", max);

    return 0;
}
```

</details>

</details>

## Practice 4: 하나는 버려

<details>
<summary>[Solution]</summary>

<details>
<summary>Sol.1</summary>

```C
#include <stdio.h>

int main() {
    int number;
    int q, w, e, r;
    int a, s, d, f;
    int max;

    printf("숫자 입력: ");
    scanf("%d", &number);

    q = number / 1000;
    w = (number / 100) % 10;
    e = (number / 10) % 10;
    r = number % 10;

    a = w * 100 + e * 10 + r;
    s = q * 100 + e * 10 + r;
    d = q * 100 + w * 10 + r;
    f = q * 100 + w * 10 + e;

    max = (a > s) ? a : s;
    max = (max > d) ? max : d;
    max = (max > f) ? max : f;

    printf("가장 큰 수: %d", max);

    return 0;
}
```

</details>

<details>
<summary>Sol.2</summary>

```C
#include <stdio.h>

int main() {
    int q, w, e, r;
    int a, s, d, f;
    int max;

    printf("숫자 입력: ");
    scanf("%1d%1d%1d%1d", &q, &w, &e, &r);

    a = w * 100 + e * 10 + r;
    s = q * 100 + e * 10 + r;
    d = q * 100 + w * 10 + r;
    f = q * 100 + w * 10 + e;

    max = (a > s) ? a : s;
    max = (max > d) ? max : d;
    max = (max > f) ? max : f;

    printf("가장 큰 수: %d", max);

    return 0;
}
```

</details>

</details>
