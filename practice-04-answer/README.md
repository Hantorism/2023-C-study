# 4회차 실습

## Practice 1: 구구단

<details>
<summary>[Solution]</summary>

```C
#include <stdio.h>

int main() {
    for (int i = 1; i <= 9; i++) {
        for (int j = 1; j <= 9; j++) {
            printf("%d * %d = %-5d", j, i, i * j);
        }
        printf("\n");
    }

    return 0;
}
```

</details>

## Practice 2: 십진수 변환

<details>
<summary>[Solution]</summary>

```C
#include <stdio.h>
#include <math.h>

int main() {
    int binary, decimal = 0;

    scanf("%d", &binary);

    for (int i = 0; binary != 0; i++) {
        decimal += (binary % 10) * (int)pow(2, i);
        binary /= 10;
    }

    printf("%d\n", decimal);

    return 0;
}
```

</details>

## Practice 3: 별찍기

<details>
<summary>[Solution]</summary>

```C
#include <stdio.h>

int main() {
    int size;

    scanf("%d", &size);

    for (int i = 0; i < size; i++) {
        for (int j = 0; j < i; j++) {
            printf(" ");
        }
        for (int j = size; j > i; j--) {
            printf("*");
        }
        printf("\n");
    }

    return 0;
}
```

</details>

## Practice 4: 피나치공

<details>
<summary>[Solution]</summary>

```C
#include <stdio.h>

int main() {
    int pizza, chicken;

    scanf("%d %d", &pizza, &chicken);

    for (int i = 1; i <= 100; i++) {
        if (i % pizza == 0 && i % chicken == 0) {
            printf("PichSet\n");
        }
        else if (i % pizza == 0) {
            printf("Pizza\n");
        }
        else if (i % chicken == 0) {
            printf("Chicken\n");
        }
        else {
            printf("%d\n", i);
        }
    }

    return 0;
}
```

</details>

## Practice 5: 평균은 넘겠지

<details>
<summary>[Solution]</summary>

```C
#include <stdio.h>

int main() {
    int testcase;

    scanf("%d", &testcase);

    while (testcase--) {
        int students;
        int score[1000];
        int sum = 0;
        int over = 0;
        double average;

        scanf("%d", &students);

        for (int i = 0; i < students; i++) {
            scanf("%d", &score[i]);
            sum += score[i];
        }

        average = (double)sum / students;

        for (int i = 0; i < students; i++) {
            if (score[i] > average) {
                over++;
            }
        }

        printf("%.3f%%\n", (double)over / students * 100);
    }

    return 0;
}
```

</details>
