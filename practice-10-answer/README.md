# 10회차 실습

## Practice 1: 동적할당 연습

<details>
<summary>[Solution 1]</summary>

```C
#include <stdio.h>
#include <stdlib.h>

int main() {
	int max, min;
	int size;
	scanf("%d", &size);

	int *arr = (int *)malloc(size * sizeof(int));
	for (int i = 0; i < size; i++) {
		scanf("%d", &arr[i]);
	}

	max = min = arr[0];
	for (int i = 0; i < size; i++) {
		max = arr[i] > max ? arr[i] : max;
		min = arr[i] < min ? arr[i] : min;
	}

	printf("%d %d", min, max);

	return 0;
}
```

</details>

## Practice 2: myStrcmp

<details>
<summary>[Solution]</summary>

```C
#include <stdio.h>
#include <stdlib.h>

int myStrcmp(char *s1, char *s2) {
	while (*s1 != '\0' || *s2 != '\0') {
		if (*s1 > *s2) {
			return 1;
		}
		else if (*s1 < *s2) {
			return -1;
		}
		else {
			s1++;
			s2++;
		}
	}
	return 0;
}

int main() {
	char *str1 = (char *)malloc(50 * sizeof(char));
	char *str2 = (char *)malloc(50 * sizeof(char));

	printf("str1: ");
	scanf("%[^\n]", str1);
	getchar();
	printf("str2: ");
	scanf("%[^\n]", str2);
	getchar();

	if (myStrcmp(str1, str2) == 0) {
		printf("identical\n");
	}
	else {
		printf("different\n");
	}

	return 0;
}
```

</details>

## Practice 3: myStrcat

<details>
<summary>[Solution]</summary>

```C
#include <stdio.h>
#include <stdlib.h>

char * myStrcat(char *s1, char *s2) {
	while (*s1 != '\0') {
		s1++;
	}
	while (*s2 != '\0') {
		*s1 = *s2;
		s1++;
		s2++;
	}
	*s1 = '\0';
	return s1;
}

int main() {
	char *str = (char *)malloc(10 * sizeof(char));
	char tempArr[100];

	printf("str: ");
	scanf("%[^\n]", str);
	getchar();
	printf("tempArr: ");
	scanf("%[^\n]", tempArr);
	getchar();

	str = (char *)realloc(str, 30 * sizeof(char));

	myStrcat(str, " of ");
	myStrcat(str, tempArr);

	printf("%s\n", str);

	return 0;
}
```

</details>

## Practice 4: 행렬의 곱셈

<details>
<summary>[Solution]</summary>

```C
#include <stdio.h>
#include <stdlib.h>

int ** createMatrix(int size) {
	int **matrix = (int **)calloc(size, sizeof(int *));

	for (int i = 0; i < size; i++) {
		matrix[i] = (int *)calloc(size, sizeof(int));
	}

	return matrix;
}

void scanMatrix(int **matrix, int size) {
	for (int i = 0; i < size; i++) {
		for (int j = 0; j < size; j++) {
			scanf("%d", &matrix[i][j]);
		}
	}
}

int ** productMatrix(int **matrix1, int **matrix2, int size) {
	int **result = createMatrix(size);

	for (int i = 0; i < size; i++) {
		for (int j = 0; j < size; j++) {
			for (int k = 0; k < size; k++) {
				result[i][j] += matrix1[i][k] * matrix2[k][j];
			}
		}
	}

	return result;
}

void printMatrix(int **matrix, int size) {
	for (int i = 0; i < size; i++) {
		for (int j = 0; j < size; j++) {
			printf("%d ", matrix[i][j]);
		}
		printf("\n");
	}
}

void freeMatrix(int **matrix, int size) {
	for (int i = 0; i < size; i++) {
		free(matrix[i]);
	}
	free(matrix);
}

int main() {
	int size;
	scanf("%d", &size);

	int **matrix1 = createMatrix(size);
	int **matrix2 = createMatrix(size);

	scanMatrix(matrix1, size);
	scanMatrix(matrix2, size);

	int **matrix3 = productMatrix(matrix1, matrix2, size);

	printMatrix(matrix3, size);

	freeMatrix(matrix1, size);
	freeMatrix(matrix2, size);
	freeMatrix(matrix3, size);

	return 0;
}
```

</details>
