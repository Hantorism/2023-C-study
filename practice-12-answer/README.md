# 12회차 실습

## Practice 1: 바탕화면

<details>
<summary>[Solution]</summary>

```C
#include <stdio.h>

int main() {
	int num;
	FILE *fp = fopen("C:\\Users\\sud0\\Desktop\\file.txt", "r");
	// sud0는 user에 해당하는 부분으로 자신의 계정을 넣으면 된다
	// \ 하나는 escape sequence이므로 \\을 사용해 \를 나타낸다

	fscanf(fp, "%d", &num);
	printf("읽은 수는 %d입니다.\n", num);
	printf("10진수: %d\n", num);
	printf("16진수: %x\n", num);

	fclose(fp);

	return 0;
}
```

</details>

## Practice 2: DM

<details>
<summary>[Solution]</summary>

```C
#include <stdio.h>
#include <string.h>

typedef enum Language {
	KOREAN, ENGLISH
} Language;

int isAlpha(char character) {
	if ((character >= 'A' && character <= 'Z') || (character >= 'a' && character <= 'z')) {
		return 1;
	}
	return 0;
}

int isSpecial(char character) {
	if (strchr(" ,'", character)) {
		return 1;
	}
	return 0;
}

int main() {
	Language language = ENGLISH;
	FILE *dm = fopen("dm.txt", "r");
	FILE *korean = fopen("korean.txt", "w");
	FILE *english = fopen("english.txt", "w");
	char buffer[1024];

	while (fgets(buffer, sizeof(buffer), dm) != NULL) {
		for (int i = 0; i < strlen(buffer) - 1; i++) {
			if (isSpecial(buffer[i])) {
				if (language == ENGLISH) {
					fprintf(english, "%c", buffer[i]);
				}
				else if (language == KOREAN) {
					fprintf(korean, "%c", buffer[i]);
				}
			} else if (isAlpha(buffer[i])) {
				if (language == KOREAN || (language == ENGLISH && i == 0)) {
					fprintf(english, "\n");
				}
				language = ENGLISH;
				fprintf(english, "%c", buffer[i]);
			} else {
				if (language == ENGLISH || (language == KOREAN && i == 0)) {
					fprintf(korean, "\n");
				}
				language = KOREAN;
				fprintf(korean, "%c", buffer[i]);
			}
		}
	}

	fclose(dm);
	fclose(korean);
	fclose(english);

	return 0;
}
```

</details>
