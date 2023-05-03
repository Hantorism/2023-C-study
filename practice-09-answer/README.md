# 9회차 실습

## Practice 1: 참조 연습

<details>
<summary>[Solution 1]</summary>

```C
#include <stdio.h>

int main() {
	int num1 = 10;
	int num2 = 20;

	int *ptr1 = &num1;
	int *ptr2 = &num2;

	printf("*ptr1: %d, *ptr2: %d\n", *ptr1, *ptr2);

	*ptr1 += 30;
	*ptr2 -= 15;

	printf("*ptr1: %d, *ptr2: %d\n", *ptr1, *ptr2);

	int *temp = ptr1;
	ptr1 = ptr2;
	ptr2 = temp;

	printf("*ptr1: %d, *ptr2: %d\n", *ptr1, *ptr2);

	return 0;
}
```

</details>

## Practice 2: 제곱

<details>
<summary>[Solution]</summary>

```C
#include <stdio.h>

void power(int *ptr) {
	*ptr *= *ptr;
}

int main() {
	int num;
	printf("정수를 입력하세요: ");
	scanf("%d", &num);

	printf("입력받은 수: %d\n", num);

	power(&num);

	printf("제곱 함수 처리 후: %d\n", num);

	return 0;
}
```

</details>

## Practice 3: 배열에서 최대값 찾기

<details>
<summary>[Solution]</summary>

```C
#include <stdio.h>

void findLargest(int *ptr, int *large) {
	*large = ptr[0];
	for (int i = 0; i < 5; i++) {
		*large = ptr[i] > *large ? ptr[i] : *large;
	}
}

int main() {
	int arr[5];
	int large;
	printf("배열의 요소를 입력하세요\n");
	for (int i = 0; i < 5; i++) {
		scanf("%d", &arr[i]);
	}

	printf("배열 내 숫자: ");
	for (int i = 0; i < 5; i++) {
		printf("%d ", arr[i]);
	}
	printf("\n");

	findLargest(arr, &large);

	printf("가장 큰 숫자: %d\n", large);

	return 0;
}
```

</details>

## Practice 4: 버블 정렬

<details>
<summary>[Solution]</summary>

```C
#include <stdio.h>

void bubbleSort(int *arr) {
	for (int i = 0; i < 7 - 1; i++) {
		for (int j = 0; j < 7 - i - 1; j++) {
			if (arr[j] > arr[j + 1]) {
				int temp = arr[j];
				arr[j] = arr[j + 1];
				arr[j + 1] = temp;
			}
		}
	}
}

int main() {
	int arr[7];
	printf("정렬 전 arr: ");
	for (int i = 0; i < 7; i++) {
		scanf("%d", &arr[i]);
	}

	bubbleSort(arr);

	printf("정렬 후 arr: ");
	for (int i = 0; i < 7; i++) {
		printf("%d ", arr[i]);
	}

	return 0;
}
```

</details>
