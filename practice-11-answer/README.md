# 11회차 실습

## Practice 1: 기울기

<details>
<summary>[Solution 1]</summary>

```C
#include <stdio.h>

typedef struct Point {
	int x;
	int y;
} Point;

int main() {
	Point point1, point2;

	printf("x, y 좌표: ");
	scanf("%d %d", &point1.x, &point1.y);

	printf("x, y 좌표: ");
	scanf("%d %d", &point2.x, &point2.y);

	printf("기울기: %.3lf\n", (double)(point2.y - point1.y) / (point2.x - point1.x));

	return 0;
}
```

</details>

## Practice 2: 구조체 배열

<details>
<summary>[Solution]</summary>

```C
#include <stdio.h>
#include <string.h>

typedef struct Professor {
	char name[100];
	char number[100];
	int age;
} Professor;

int main() {
	Professor professors[3];
	char target[100];

	for (int i = 0; i < 3; i++) {
		printf("저장할 교수님의 정보를 입력하세요\n");
		printf("이름: ");
		scanf("%s", professors[i].name);
		printf("전화번호: ");
		scanf("%s", professors[i].number);
		printf("연구실: ");
		scanf("%d", &professors[i].age);
	}

	printf("정보를 볼 교수님의 이름을 입력하세요: ");
	scanf("%s", target);
	for (int i = 0; i < 3; i++) {
		if (strcmp(target, professors[i].name) == 0) {
			printf("이름: %s\n", professors[i].name);
			printf("전화번호: %s\n", professors[i].number);
			printf("연구실: %d\n", professors[i].age);
		}
	}

	return 0;
}
```

</details>

## Practice 3: 구조체 정렬

<details>
<summary>[Solution]</summary>

```C
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

typedef struct Student {
	char name[100];
	int number;
} Student;

void sortByName(Student *students) {
	for (int i = 0; i < 3; i++) {
		for (int j = 0; j < 3 - i; j++) {
			if (strcmp(students[j].name, students[j + 1].name) > 0) {
				Student temp = students[j];
				students[j] = students[j + 1];
				students[j + 1] = temp;
			}
		}
	}
}

void sortByNumber(Student *students) {
	for (int i = 0; i < 3; i++) {
		for (int j = 0; j < 3 - i; j++) {
			if (students[j].number > students[j + 1].number) {
				Student temp = students[j];
				students[j] = students[j + 1];
				students[j + 1] = temp;
			}
		}
	}
}

void printStudents(Student *students) {
	for (int i = 0; i < 4; i++) {
		printf("%d %s\n", students[i].number, students[i].name);
	}
	printf("\n");
}

int main() {
	Student *students = (Student *)malloc(4 * sizeof(Student));

	for (int i = 0; i < 4; i++) {
		printf("학생 %d의 학번 입력: ", i + 1);
		scanf("%d", &students[i].number);
		printf("학생 %d의 이름 입력: ", i + 1);
		scanf("%s", students[i].name);
	}
	printf("\n");

	printf("이름 순 정렬\n");
	sortByName(students);
	printStudents(students);

	printf("학번 순 정렬\n");
	sortByNumber(students);
	printStudents(students);

	free(students);

	return 0;
}
```

</details>

## Practice 4: 구조체도 배웠는데 좋아 게임할까

<details>
<summary>[Solution]</summary>

```C
#include <stdio.h>
#include <string.h>

typedef struct Student {
	char name[5];
	char lover[3][5];
} Student;

int main() {
	Student students[3];

	for (int i = 0; i < 3; i++) {
		scanf("%s -> ", students[i].name);
		for (int j = 0; j < 3; j++) {
			scanf("%s", students[i].lover[j]);
		}
	}

	for (int i = 0; i < 3; i++) {
		for (int j = 0; j < 3; j++) {
			for (int k = 0; k < 3; k++) {
				if (i == k) {
					continue;
				}
				if (strcmp(students[i].lover[j], students[k].name) == 0) {
					for (int l = 0; l < 3; l++) {
						if (strcmp(students[k].lover[l], students[i].name) == 0) {
							printf("%s %s\n", students[i].name, students[i].lover[j]);
						}
					}
				}
			}
		}
	}

	return 0;
}
```

</details>
