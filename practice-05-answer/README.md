# 5회차 실습

## Practice 0: 기본 배열 활용

<details>
<summary>[Solution]</summary>

```C
#include <stdio.h>

int main() {
    int arr[3];
    int count = 0;
    int sum = 0;

    while (1) {
        scanf("%d", &arr[count]);
        if (arr[count] == -1) {
            break;
        }
        sum += arr[count++];
    }

    printf("count: %d, sum: %d\n", count, sum);

    return 0;
}
```

</details>

## Practice 1: 거꾸로 배열

<details>
<summary>[Solution]</summary>

```C
#include <stdio.h>

int main() {
    int arr[10];

    printf("Input  : ");
    for (int i = 0; i < 10; i++) {
        scanf("%d", &arr[i]);
    }

    printf("Output1: ");
    for (int i = 9; i >= 0; i--) {
        printf("%d ", arr[i]);
    }
    printf("\n");

    arr[2] = 999;

    printf("Output2: ");
    for (int i = 9; i >= 0; i--) {
        printf("%d ", arr[i]);
    }
    printf("\n");

    return 0;
}
```

</details>

## Practice 2: 구구단표

<details>
<summary>[Solution]</summary>

```C
#include <stdio.h>

int main() {
    int arr[9][9];

    for (int i = 0; i < 9; i++) {
        for (int j = 0; j < 9; j++) {
            arr[i][j] = (i + 1) * (j + 1);
        }
    }

    for (int i = 0; i < 9; i++) {
        for (int j = 0; j < 9; j++) {
            printf("%3d", arr[i][j]);
        }
        printf("\n");
    }

    return 0;
}
```

</details>

## Practice 3: 호구조사

<details>
<summary>[Solution]</summary>

```C
#include <stdio.h>

int main() {
    int apart[5][2];

    for (int i = 0; i < 5; i++) {
        for (int j = 0; j < 2; j++) {
            printf("%d0%d호에 몇명이 삽니까? ", i + 1, j + 1);
            scanf("%d", &apart[i][j]);
        }
    }

    printf("        1호   2호\n");
    printf("==================\n");

    for (int i = 4; i >= 0; i--) {
        printf("%d층", i + 1);
        for (int j = 0; j < 2; j++) {
            printf("%6d", apart[i][j]);
        }
        printf("\n");
    }

    return 0;
}
```

</details>

## Practice 4: 전치 행렬

<details>
<summary>[Solution]</summary>

```C
#include <stdio.h>

int main() {
    int matrix[4][4];

    for (int i = 0; i < 4; i++) {
        for (int j = 0; j < 4; j++) {
            matrix[i][j] = 4 * i + j + 1;
        }
    }

    for (int i = 0; i < 4; i++) {
        for (int j = 0; j < 4; j++) {
            printf("%3d", matrix[i][j]);
        }
        printf("\n");
    }
    printf("\n");

    for (int i = 0; i < 4; i++) {
        for (int j = i + 1; j < 4; j++) {
            int temp;
            temp = matrix[i][j];
            matrix[i][j] = matrix[j][i];
            matrix[j][i] = temp;
        }
    }

    for (int i = 0; i < 4; i++) {
        for (int j = 0; j < 4; j++) {
            printf("%3d", matrix[i][j]);
        }
        printf("\n");
    }
    printf("\n");

    return 0;
}
```

</details>

## Practice 5: 2007년

<details>
<summary>[Solution]</summary>

```C
#include <stdio.h>

int main() {
    int months[13] = {0, 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31};
    int month, day;
    int sum = 0;

    scanf("%d %d", &month, &day);

    for (int i = 0; i < month; i++) {
        sum += months[i];
    }
    sum += day;

    switch (sum % 7) {
        case 1: printf("MON\n"); break;
        case 2: printf("TUE\n"); break;
        case 3: printf("WED\n"); break;
        case 4: printf("THU\n"); break;
        case 5: printf("FRI\n"); break;
        case 6: printf("SAT\n"); break;
        case 0: printf("SUN\n"); break;
    }

    return 0;
}
```

</details>
