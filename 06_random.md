# random

## 题目

```
Daddy, teach me how to use random value in programming!

ssh random@pwnable.kr -p2222 (pw:guest)
```

## 源码

```c
#include <stdio.h>

int main(){
	unsigned int random;
	random = rand();	// random value!

	unsigned int key=0;
	scanf("%d", &key);

	if( (key ^ random) == 0xdeadbeef ){
		printf("Good!\n");
		system("/bin/cat flag");
		return 0;
	}

	printf("Wrong, maybe you should try 2^32 cases.\n");
	return 0;
}
```



```
vi /tmp/random.c

#include<stdio.h>
#include<stdlib.h>
int main(){
    unsigned int random;
    random=rand();
	printf("%u\n",random ^ 0xdeadbeef);
}
gcc ./random.c
./a.out

dom@ubuntu:~$ ./random 


-1255736440
Good!
Mommy, I thought libc random is unpredictable...

```