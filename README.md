# Hello Audiences

Nutchanon's space for announcement.

# e-lab
for lab 05 or later.
### 05-1-01
``` 
#include <stdio.h>
#include <stdlib.h>
int main(int argc , char *argv[]) {
    if (argc < 2) {
        fprintf(stderr,"Usage: %s num...\n", argv[0]);
        return 1;
    }
    int sum=0,i;
    int number;
    for (i=1 ; i<argc ; i++) {
        number = atoi(argv[i]);
        sum += number;
    }
    printf("%d\n",sum);
    return 0;
}
```
### 05-1-02
``` 
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(int argc, char *argv[]) {
    if (argc < 3) {
        fprintf(stderr, "Usage: %s num...\n", argv[0]);
        exit(1);
    }
    char *format_str = getenv("FORMAT");
    int format_available = (format_str != NULL) && (strcmp(format_str,"") != 0);
    int num,sum=0;
    for (int i=1 ; i<argc ; i++) {
        num = atoi(argv[i]);
        sum += num;
    }
    if (format_available) {
        printf(format_str , sum);
        printf("\n");
    }
    else {
        printf("%d\n" , sum);
    }
    return 0;
}
```
### 05-1-03
```
#ifndef BANNER_H
#define BANNER_H
void banner_vertical(char *);
void banner_horizontal(char *);
#endif
```
```
#include "banner.h"
#include <stdio.h>
#include <string.h>
void banner_vertical(char *text) {
    int i=0;
    printf("+---+\n");
    while (*text != '\0') {
        printf("| %c |\n" , *text);
        text++;
    }
    printf("+---+\n");
}

void banner_horizontal(char *text) {
    char *tmp = text;
    // line 1
    printf("+-");
    while (*tmp != '\0') {
        printf("-");
        tmp++;
    }
    printf("-+\n");

    // line 2
    tmp = text;
    printf("| ");
    while (*tmp != '\0') {
        printf("%c" , *tmp);
        tmp++;
    }
    printf(" |\n");

    tmp = text;

    // line 3
    printf("+-");
    while (*tmp != '\0') {
        printf("-");
        tmp++;
    }
    printf("-+\n");
}
```
```
gcc -c banner.c
gcc -c show-banner.c
gcc -o show-banner show-banner.o banner.o
```
### 05-1-04
credit: P
```
#include "practicum.h"
#include<stdio.h>
#include<stdlib.h>
#include<string.h>

int main(int argc,char **argv){
    int result;
    if(argc <3){
        fprintf(stderr,"Usage: %s type name\n",argv[0]);
        exit(1);
    }
    else if(strcmp(argv[1],"topic")!=0 && strcmp(argv[1],"lecturer")!=0){
        fprintf(stderr,"Invalid type\n");
        exit(2);
    }

    if(strcmp(argv[1],"topic")==0){
        result = practicum_get_topic_id(argv[2]);
    }
    else if(strcmp(argv[1],"lecturer")==0){
        result = practicum_get_lecturer_id(argv[2]);
    }

    if(result!=-1){
        printf("%d\n",result);
    }
    else{
        fprintf(stderr,"Name not found\n");
        exit(3);
    }
} 
```
```
gcc -c  practicum-info.c -I practicum-1.0.0/include/
gcc -static -o practicum-info-static practicum-info.o practicum-1.0.0/lib/libpracticum.a 
```
```
gcc -c practicum-info.c -I practicum-1.0.0/include/
gcc -o practicum-info-dynamic practicum-info.o practicum-1.0.0/lib/libpracticum.so
```
```
./practicum-info-dynamic practicum-1.0.0/lib/libpracticum.so
```
### 05-2-01
```
myprog : main.o mod2.o mod1.o
    gcc -o myprog main.o mod1.o mod2.o
main.o : main.c mod2.h
    gcc -c main.c
mod2.o : mod1.h mod2.h mod2.c
    gcc -c mod2.c
mod1.o : mod1.h mod1.c
    gcc -c mod1.c
```
### 05-2-02
```
.PHONY: clean bundle
bundle: main.c mod1.c mod1.h mod2.c mod2.h
    tar zcf source.tgz main.c mod1.c mod1.h mod2.c mod2.h
clean:
    rm -f *.o
    rm -f source.tgz
```
### 05-2-03
```
.PHONY: get-fullname

get-fullname:
    @grep "^${USER}:" /etc/passwd | cut -d: -f5,5 | cut -d, -f1,1
```
### 05-2-04
```
%.out: %.sh
    @sh $< >> $@
```
