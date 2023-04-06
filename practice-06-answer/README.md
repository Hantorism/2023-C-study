# 6회차 실습

## Practice 1: 최솟값 최댓값

<details>
<summary>[Solution 1]</summary>

```C
#include <stdio.h>
#include <limits.h>

int getMin(int min, int current) {
    return (current < min) ? current : min;
}

int getMax(int max, int current) {
    return (current > max) ? current : max;
}

int main() {
    int arr[5];
    int min = INT_MAX;
    int max = INT_MIN;

    printf("배열 입력: ");
    for (int i = 0; i < 5; i++) {
        scanf("%d", &arr[i]);
    }

    for (int i = 0; i < 5; i++) {
        min = getMin(min, arr[i]);
    }

    for (int i = 0; i < 5; i++) {
        max = getMax(max, arr[i]);
    }

    printf("배열의 최솟값: %d\n", min);
    printf("배열의 최댓값: %d\n", max);

    return 0;
}
```

</details>

<details>
<summary>[Solution 2]</summary>

```C
#include <stdio.h>

int getMin(int min, int current) {
    return (current < min) ? current : min;
}

int getMax(int max, int current) {
    return (current > max) ? current : max;
}

int main() {
    int arr[5];
    int min;
    int max;

    printf("배열 입력: ");
    for (int i = 0; i < 5; i++) {
        scanf("%d", &arr[i]);
    }

    min = arr[0];
    for (int i = 0; i < 5; i++) {
        min = getMin(min, arr[i]);
    }

    max = arr[0];
    for (int i = 0; i < 5; i++) {
        max = getMax(max, arr[i]);
    }

    printf("배열의 최솟값: %d\n", min);
    printf("배열의 최댓값: %d\n", max);

    return 0;
}
```

</details>

## Practice 2: 함수로 더하기

<details>
<summary>[Solution]</summary>

```C
#include <stdio.h>

void printMessage() {
    printf("두 개의 정수를 입력하시면 덧셈 결과가 출력됩니다.\n");
}

int scanNumber() {
    int number;
    printf("정수 입력: ");
    scanf("%d", &number);
    return number;
}

int addNumbers(int num1, int num2) {
    return num1 + num2;
}

void printResult(int sum) {
    printf("덧셈 결과 출력: %d\n", sum);
}

int main() {
    int num1, num2, sum;

    printMessage();

    num1 = scanNumber();
    num2 = scanNumber();

    sum = addNumbers(num1, num2);

    printResult(sum);

    return 0;
}
```

</details>

## Practice 3: 피보나치 수열

<details>
<summary>[Solution]</summary>

```C
#include <stdio.h>

int fibonacci(int term) {
    if (term == 1 || term == 2) {
        return 1;
    }
    else {
        return fibonacci(term - 1) + fibonacci(term - 2);
    }
}

int main() {
    int term;

    printf("피보나치 수열에서 구하고 싶은 항을 입력하세요: ");
    scanf("%d", &term);

    printf("fib(%d) = %d\n", term, fibonacci(term));

    return 0;
}
```

</details>

## Practice 4: 조합

<details>
<summary>[Solution]</summary>

```C
#include <stdio.h>

int combination(int n, int r) {
    if (n == r || r == 0) {
        return 1;
    }
    else {
        return combination(n - 1, r - 1) + combination(n - 1, r);
    }
}

int main() {
    int n, r;

    scanf("%d C %d", &n, &r);

    printf("%d\n", combination(n, r));

    return 0;
}
```

</details>
