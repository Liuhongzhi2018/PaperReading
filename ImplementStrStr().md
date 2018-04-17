#	Implement strStr()   

## 问题分析
Implement strStr().

Return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.

实现 strStr() 函数。

给定一个 haystack 字符串和一个 needle 字符串，在 haystack 字符串中找出 needle 字符串出现的第一个位置 (从0开始)。如果不存在，则返回  -1。

## 代码实现
``` C
void nextStr(char *needle, int* a) {
	int i = 0;
	int j = -1;
	a[0] = -1;
	while (needle[i]!='\0') {
		if (j == -1 || needle[j] == needle[i]) {
			j++;
			i++;
			a[i] = j;
		}
		else {
			j = a[j];
		}
	}
}
int strStr(char* haystack, char* needle) {
	int i = 0;
	int j = 0;
	int n = strlen(needle);
	int *a;
	a = (int*)malloc(sizeof(int) * (n + 1));
	nextStr(needle, a);
	while (j == -1 ||((haystack[i]!='\0') &&(needle[j]!='\0'))) {
		if (j == -1 || haystack[i] == needle[j]) {
			j++; 
			i++;
		}
		else {
			j = a[j];
		}
	}
	if (needle[j]!='\0')  return -1;
	else return   i - n;
}
```

## 总结体会

本题要求从一个字符串中，找出另一字符串第一次出现的位置。

解题思路是根据待确定位置的字符串构建一个数组，将字符串的元素位置保存为对应所在位置数值，然后在字符串中查找是否包含待确定位置的字符串，若存在待求字符串，则返回位置信息。
