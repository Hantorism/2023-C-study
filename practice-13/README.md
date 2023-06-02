# 13회차 프로젝트

## ATM 구현

### [요구사항]

계좌의 정보를 저장할 `Account` 구조체를 만든다.

`Account` 구조체는 계좌번호, 비밀번호 잔액을 저장해야 한다.

ATM의 여러 기능들을 정의하는 `Function` 열거형을 만든다.

`Function` 열거형은 login, retrieve balance, deposit, withdraw, transfer, register, delete, end 총 8개의 상수를 가진다.

현재 계좌의 정보를 가지는 `currentAccount` 변수와 저장하고 있는 계좌들의 개수를 나타내는 `accountNum` 변수를 전역변수로 선언한다.

`main()`의 처음에는 등록할 계좌의 개수를 입력받고 계좌들의 정보를 저장할 `accounts`를 포인터 변수로 만들고 등록할 계좌의 수만큼 동적할당 받는다.

동적할당이 끝나면 등록할 계좌의 수만큼 계좌를 등록한다.

이후에는 사용자가 ATM의 기능들 중 하나를 선택해서 실행한다.

이 기능들은 사용자가 종료를 선택하기 전까지 반복해서 출력되고 선택할 수 있어야 한다.

ATM이 가지는 기능들은 총 8개가 있다.

1. `login()`

   사용자로부터 `account`와 `password`를 입력받는다.

   입력받은 `account`가 `accounts`에 있으면 비밀번호를 검사한다.

   비밀번호가 맞으면 로그인이 성공했다는 정보를 저장하고 `currentAccount`를 그 계좌로 설정한다.

2. `retrieveBalance()`

   현재 계좌에 있는 잔액을 출력해준다.

   이 함수는 로그인해야 실행될 수 있다.

3. `deposit()`

   사용자로부터 입금할 금액를 입력받는다.

   현재 계좌의 잔액에 입력받은 금액을 더한다.

   이 함수는 로그인해야 실행될 수 있다.

4. `withdraw()`

   사용자로부터 출금할 금액를 입력받는다.

   현재 계좌의 잔액에 입력받은 금액을 뺀다.

   현재 계좌의 잔액보다 많은 금액을 출금할 수 없다.

   이 함수는 로그인해야 실행될 수 있다.

5. `transfer()`

   사용자로부터 이체할 금액와 `account`를 입력받는다.

   `currentAccount`의 잔액보다 이체할 금액이 많으면 에러가 발생한다.

   `accounts`에서 이체할 계좌를 찾고 이체한다.

   이 함수는 로그인해야 실행될 수 있다.

6. `registerAccount()`

   사용자로부터 등록할 계좌의 정보를 입력받는다.

   이 함수가 실행되기 전 `accountNum`이 증가되어야 한다.

   `accounts`는 현재 등록되어 있는 계좌의 개수만큼만 저장할 수 있도록 재할당한다.

7. `deleteAccount()`

   사용자로부터 삭제할 계좌의 정보를 입력받는다.

   `accounts`에서 삭제할 계좌를 찾았고 비밀번호도 맞았다면 `accounts`에서 그 계좌를 삭제한다.

   삭제하는 방법은 그 인덱스부터 끝까지 한 칸 씩 앞으로 당기면서 덮어씌움으로써 삭제한다.

   이 함수가 실행되고난 후 `accountNum`이 감소되어야 한다.

   `accounts`는 현재 등록되어 있는 계좌의 개수만큼만 저장할 수 있도록 재할당한다.

8. `end`

   이 기능을 위해 따로 함수가 필요하진 않고 반복하고 있는 메인메뉴를 종료시키는 시그널을 주면 된다.

만약 사용자가 1~8이 아닌 다른 숫자를 입력했다면 올바른 기능을 선택하라는 메시지를 출력하고 다시 반복한다.

모든 기능에는 사용자가 쉽게 사용할 수 있게 적절한 설명과 오류 상황일 때 에러 메시지를 보여줘야 한다.

<details>
<summary>[Skeleton]</summary>

```C
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#define MAX_LEN 30

typedef struct Account {
    char password[MAX_LEN];
    char account[MAX_LEN];
    int balance;
} Account;

typedef enum Function {
    LOGIN = 1, RETRIEVE_BALANCE, DEPOSIT, WITHDRAW, TRANSFER, REGISTER, DELETE, END
} Function;

Account currentAccount;
int accountNum;

void login(Account *accounts, int *isLogin) {
    //TODO
}

void retrieveBalance() {
    //TODO
}

void deposit() {
    //TODO
}

void withdraw() {
    //TODO
}

void transfer(Account *accounts) {
    //TODO
}

void registerAccount(Account *accounts, int index) {
    //TODO
}

void deleteAccount(Account *accounts) {
    //TODO
}

int main() {
    printf("==========[Bank System]==========\n\n");
    printf("등록할 계좌 수를 입력해주세요: ");
    scanf("%d", &accountNum);
    Account *accounts = (Account *)malloc(accountNum * sizeof(Account));
    printf("총 %d개의 계좌를 등록할 수 있습니다\n\n", accountNum);

    for (int i = 0; i < accountNum; i++) {
        //TODO
        printf("\n");
    }

    Function function;
    int isLogin = 0;
    for (int repeat = 1; repeat != 0;) {
        printf("==========[Main Menu]==========\n");
        printf("현재 계좌: %s\n", currentAccount.account);
        printf("1. 로그인(계좌 변경)\n");
        printf("2. 잔액 조회\n");
        printf("3. 입금\n");
        printf("4. 출금\n");
        printf("5. 이체\n");
        printf("6. 계좌 등록\n");
        printf("7. 계좌 삭제\n");
        printf("8. 종료\n");
        printf("원하는 기능을 입력해주세요: ");
        scanf("%d", &function);

        switch (function) {
            case LOGIN:
                //TODO
                break;
            case RETRIEVE_BALANCE:
                //TODO
                break;
            case DEPOSIT:
                //TODO
                break;
            case WITHDRAW:
                //TODO
                break;
            case TRANSFER:
                //TODO
                break;
            case REGISTER:
                //TODO
                break;
            case DELETE:
                //TODO
                break;
            case END:
                //TODO
                break;
            default:
                printf("올바른 기능을 선택해주세요\n");
                break;
        }
        printf("\n");
    }

    free(accounts);
    return 0;
}

```

</details>

<details>
<summary>[Solution]</summary>

```C
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#define MAX_LEN 30

typedef struct Account {
    char password[MAX_LEN];
    char account[MAX_LEN];
    int balance;
} Account;

typedef enum Function {
    LOGIN = 1, RETRIEVE_BALANCE, DEPOSIT, WITHDRAW, TRANSFER, REGISTER, DELETE, END
} Function;

Account currentAccount;
int accountNum;

void login(Account *accounts, int *isLogin) {
    char account[MAX_LEN];
    char password[MAX_LEN];
    printf("접속할 계좌번호를 입력해주세요: ");
    scanf("%s", account);

    for (int i = 0; i < accountNum; i++) {
        if (strcmp(accounts[i].account, account) == 0) {
            printf("비밀번호를 입력해주세요: ");
            scanf("%s", password);

            if (strcmp(accounts[i].password, password) == 0) {
                printf("해당 계좌로 접속합니다\n");
                *isLogin = 1;
                currentAccount = accounts[i];
            } else {
                printf("잘못된 비밀번호를 입력했습니다\n");
                *isLogin = 0;
            }
            return;
        }
    }
    printf("등록된 계좌 중 일치하는 계좌가 없습니다\n");
    *isLogin = 0;
}

void retrieveBalance() {
    printf("계좌에 있는 잔액은 %d만원입니다\n", currentAccount.balance);
}

void deposit() {
    int amount;
    printf("얼마를 입금하시겠습니까(만원 단위): ");
    scanf("%d", &amount);
    currentAccount.balance += amount;
    printf("%d만원이 입금되었습니다\n", amount);
}

void withdraw() {
    int amount;
    printf("얼마를 출금하시겠습니까(만원 단위): ");
    scanf("%d", &amount);

    if (amount > currentAccount.balance) {
        printf("현재 계좌의 잔액보다 많은 돈을 출금할 수 없습니다\n");
        return;
    }

    currentAccount.balance -= amount;
    printf("%d만원이 출금되었습니다\n", amount);
}

void transfer(Account *accounts) {
    int amount;
    char account[MAX_LEN];

    printf("얼마를 이체하시겠습니까(만원 단위): ");
    scanf("%d", &amount);

    if (amount > currentAccount.balance) {
        printf("잔액이 부족합니다\n");
        return;
    }

    printf("이체할 계좌번호를 입력해주세요: ");
    scanf("%s", account);

    for (int i = 0; i < accountNum; i++) {
        if (strcmp(accounts[i].account, account) == 0) {
            currentAccount.balance -= amount;
            accounts[i].balance += amount;
            printf("%d만원을 %s에 이체했습니다\n", amount, accounts[i].account);
            return;
        }
    }
    printf("등록된 계좌 중 일치하는 계좌가 없습니다\n");
}

void registerAccount(Account *accounts, int index) {
    printf("등록할 계좌의 정보를 입력해주세요\n");

    printf("계좌번호: ");
    scanf("%s", accounts[index].account);

    printf("비밀번호: ");
    scanf("%s", accounts[index].password);

    printf("잔액(만원 단위): ");
    scanf("%d", &accounts[index].balance);

    printf("해당 계좌가 등록되었습니다\n");
}

void deleteAccount(Account *accounts) {
    char account[MAX_LEN];
    char password[MAX_LEN];
    printf("삭제할 계좌번호를 입력해주세요: ");
    scanf("%s", account);

    for (int i = 0; i < accountNum; i++) {
        if (strcmp(accounts[i].account, account) == 0) {
            printf("비밀번호를 입력해주세요: ");
            scanf("%s", password);

            if (strcmp(accounts[i].password, password) == 0) {
                for (int j = i; j < accountNum - 1; j++) {
                    accounts[j] = accounts[j + 1];
                }
                printf("해당 계좌가 삭제되었습니다\n");
            } else {
                printf("잘못된 비밀번호를 입력했습니다\n");
            }
            return;
        }
    }
    printf("등록된 계좌 중 일치하는 계좌가 없습니다\n");
}

int main() {
    printf("==========[Bank System]==========\n\n");
    printf("등록할 계좌 수를 입력해주세요: ");
    scanf("%d", &accountNum);
    Account *accounts = (Account *)malloc(accountNum * sizeof(Account));
    printf("총 %d개의 계좌를 등록할 수 있습니다\n\n", accountNum);

    for (int i = 0; i < accountNum; i++) {
        registerAccount(accounts, i);
        printf("\n");
    }

    Function function;
    int isLogin = 0;
    for (int repeat = 1; repeat != 0;) {
        printf("==========[Main Menu]==========\n");
        printf("현재 계좌: %s\n", currentAccount.account);
        printf("1. 로그인(계좌 변경)\n");
        printf("2. 잔액 조회\n");
        printf("3. 입금\n");
        printf("4. 출금\n");
        printf("5. 이체\n");
        printf("6. 계좌 등록\n");
        printf("7. 계좌 삭제\n");
        printf("8. 종료\n");
        printf("원하는 기능을 입력해주세요: ");
        scanf("%d", &function);

        switch (function) {
            case LOGIN:
                login(accounts, &isLogin);
                break;
            case RETRIEVE_BALANCE:
                if (isLogin) {
                    retrieveBalance();
                } else {
                    printf("로그인 후 시도해주시기 바랍니다\n");
                }
                break;
            case DEPOSIT:
                if (isLogin) {
                    deposit();
                } else {
                    printf("로그인 후 시도해주시기 바랍니다\n");
                }
                break;
            case WITHDRAW:
                if (isLogin) {
                    withdraw();
                } else {
                    printf("로그인 후 시도해주시기 바랍니다\n");
                }
                break;
            case TRANSFER:
                if (isLogin) {
                    transfer(accounts);
                } else {
                    printf("로그인 후 시도해주시기 바랍니다\n");
                }
                break;
            case REGISTER:
                accountNum++;
                accounts = (Account *)realloc(accounts, accountNum * sizeof(Account));
                registerAccount(accounts, accountNum - 1);
                break;
            case DELETE:
                deleteAccount(accounts);
                accountNum--;
                accounts = (Account *)realloc(accounts, accountNum * sizeof(Account));
                break;
            case END:
                printf("ATM을 종료합니다\n");
                repeat = 0;
                break;
            default:
                printf("올바른 기능을 선택해주세요\n");
                break;
        }
        printf("\n");
    }

    free(accounts);
    return 0;
}
```

</details>
