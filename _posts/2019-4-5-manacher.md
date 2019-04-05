---
layout: post
title: 2019-4-5 manacher

date: 2019-4-5
categories: blog
tags: [,]
description: 
---

---------------------

```c++
void change(){
	S[0] = '#';
	int len = strlen(S1);
	For(i,0,len){
		S[2 * (i + 1) - 1] = S1[i];
		S[2 * (i + 1)] = '#';
	}
}
int len[MAXN << 1];
void manacher(){
	int maxright = 0,mid = 0;
	int l = strlen(S);
	For(i,0,l){
		if (i <= maxright)	len[i] = min(len[(mid << 1) - i],maxright - i + 1);
		else	len[i] = 1;
		while(i + len[i] < l && i - len[i] >= 0 && S[i + len[i]] == S[i - len[i]])	len[i]++;
		if (len[i] + i - 1 > maxright){
			maxright = len[i] + i - 1;
			mid = i;
		}
	}
}
```