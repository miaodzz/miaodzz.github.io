---
title: Project Euler Problem1-50 刷题笔记
date: 2020-08-29 22:45:01
tags:
categories: Project Euler
---
[Github Repo](https://github.com/miaodzz/proejct_euler) 

## 线性筛法

    def problem50(): #线性筛法
        prime=[]
        is_pri=[1 for i in range(1000000)]

        for i in range(2,1000000):
            if is_pri[i]:
                prime.append(i)
                for j in range(i*i,1000000,i):
                    is_pri[j]=0

        maxlen=0
        ans=0
        for i in range(1,len(prime)):
            s=0
            for j in range(i,len(prime)):
                s+=prime[j]
                if s>=1000000:
                    break
                if is_pri[s] and j-i+1>maxlen:
                    maxlen=j-i+1
                    ans=s
        print(ans)


## 素因子
    def find_prime_factors(n):
        i=2
        factors={}
        while i*i<=n:
            while n%i==0:
                factors[i]=1
                n//=i
            i+=1
        if n>0:
            factors[n]=1
        return list(factors.keys())

## python迭代
    from itertools import permutations
    permutations(listxx)