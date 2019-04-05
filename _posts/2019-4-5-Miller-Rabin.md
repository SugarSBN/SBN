---
layout: post
title: 2019-4-5 Miller_Rabin

date: 2019-4-5
categories: blog
tags: [,]
description: 
---

---------------------

```c++
namespace Miller_Rain{
	int base[5] = {2,3,7,61,24251};	
	inline bool Miller_Rabin(ull X){
		ull A = X - 1,B = 0;
		while(!(A & 1))	B++,A >>= 1;
		For(i,0,5)	if (X == base[i])	return 1;
		For(i,0,5){
			ull res = qpow(base[i],A,X);
			if (res == 1 || res == X - 1)	continue;
			int j = 1;
			for (j = 1;j <= B;j++)	{
				(res *= res) %= X;
				if (res == X - 1)	break;
			}	
			if (j > B)	return 0;
		}
		return 1;
	}
};
```