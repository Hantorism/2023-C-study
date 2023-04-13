# 6회차 실습

## Practice 1: 끊어서 출력

<details>
<summary>[Solution 1]</summary>

```C
#include <stdio.h>
#include <string.h>

int main() {
	char str[100];

	scanf("%[^\n]", str);

	for (int i = 0; i < (int)strlen(str); i++) {
		printf("%c", str[i]);

		if (i % 10 == 9) {
			printf("\n");
		}
	}

	return 0;
}
```

</details>

## Practice 2: 호구조사

<details>
<summary>[Solution]</summary>

```C
#include <stdio.h>
#include <string.h>

int main() {
	char name[5][2][100];

	for (int i = 0; i < 5; i++) {
		for (int j = 0; j < 2; j++) {
			printf("%d0%d호에 누가 삽니까? ", i + 1, j + 1);
			scanf("%s", name[i][j]);
		}
	}

	printf("        1호       2호\n");
	printf("=========================\n");
	for (int i = 4; i >= 0; i--) {
		printf("%d층\t%-10s%-10s\n", i + 1, name[i][0], name[i][1]);
	}

	return 0;
}
```

</details>

## Practice 3: string.h 1

<details>
<summary>[Solution]</summary>

```C
#include <stdio.h>
#include <string.h>

int main() {
	char str[100];

	scanf("%s", str);

	printf("%d\n", (int)strlen(str));

	return 0;
}
```

</details>

## Practice 4: string.h 2

<details>
<summary>[Solution]</summary>

```C
#include <stdio.h>
#include <string.h>

int main() {
	char str1[100];
	char str2[100];

	scanf("%s %s", str1, str2);

	if (strcmp(str1, str2) == 0) {
		printf("같다\n");
	}
	else {
		printf("다르다\n");
	}

	return 0;
}
```

</details>

## Practice 5: string.h 3

<details>
<summary>[Solution]</summary>

```C
#include <stdio.h>
#include <string.h>

int main() {
	char str1[100];
	char str2[100];

	scanf("%s", str1);

	strcpy(str2, str1);

	printf("%s %s", str1, str2);

	return 0;
}
```

</details>

## Practice 6: string.h 4

<details>
<summary>[Solution]</summary>

```C
#include <stdio.h>
#include <string.h>

int main() {
	char str1[100];
	char str2[100];

	scanf("%[^\n]", str1);
	getchar();
	scanf("%[^\n]", str2);
	getchar();

	strcat(str1, str2);

	printf("%s", str1);

	return 0;
}
```

</details>

## Practice 7: string.h 5

<details>
<summary>[Solution]</summary>

```C
#include <stdio.h>
#include <string.h>

int main() {
	char target[100];
	char search[100];

	scanf("%[^\n]", target);
	getchar();
	scanf("%[^\n]", search);
	getchar();

	if (strstr(target, search) != NULL) {
		printf("있네용\n");
	}
	else {
		printf("없네용\n");
	}

	return 0;
}
```

</details>

## Practice 8: 이름순으로 정렬해주세요 학우님들

<details>
<summary>[Solution]</summary>

```C
#include <stdio.h>
#include <string.h>

int main() {
	char student1[20];
	char student2[20];
	char student3[20];
	char temp[20];

	printf("Input: ");
	scanf("%s", student1);
	scanf("%s", student2);
	scanf("%s", student3);

	if (strcmp(student1, student2) > 0) {
		strcpy(temp, student1);
		strcpy(student1, student2);
		strcpy(student2, temp);
	}
	if (strcmp(student2, student3) > 0) {
		strcpy(temp, student2);
		strcpy(student2, student3);
		strcpy(student3, temp);
	}
	if (strcmp(student1, student2) > 0) {
		strcpy(temp, student1);
		strcpy(student1, student2);
		strcpy(student2, temp);
	}

	strcat(student1, "학우님");
	strcat(student2, "학우님");
	strcat(student3, "학우님");

	printf("Output: %s %s %s\n", student1, student2, student3);

	return 0;
}
```

</details>
