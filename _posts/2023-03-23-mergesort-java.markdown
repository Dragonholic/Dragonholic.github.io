---
layout: post
title:  "(알고리즘)mergesort 자바"
date:   2023-03-23 13:20:46 +0900
categories: algorithm
tag: [algorithm]
---

# (Algorithm)Mergesort - Java 

## 1.Mergesort(합병정렬)가 뭐지 정렬에 이름을 왜 붙이지?

mergesort는 희대의 천재 폰 노이만이 고안한 방법으로 

한마디로 말해 정렬을 빠르게 하는 방법중 하나 라는 소리이다.

여기서 왜 단순히 정렬을 하는데 굳이 빠르게라는 단어를 붙혔는가 생각을 해보자 

우리 인간들은 정렬을 할때 어떻게 할까  생각해 본사람은 많지 않을 것이다.

오름차순으로 정렬해본다고 생각 해보았을때 단순하게 1부터 시작해서 2를 찾고 3을 찾을 것이다. 

이때 적당한(한눈에 들어올만한)정도의 양이면 말그대로 한눈에 보고 1부터 시작하여 찾겠지만 이 숫자가 거대해지면 이야기가 달라진다. 하나하나 뒤져가면서 다음숫자를 찾고 다음숫자를 찾을것이다. 

심지어 너무나 많은 숫자에 방금 보았던 숫자의 위치 마저 까먹어버린 상황이라면 사태는 걷잡을 수 없어 질 것이다.

우리들의 눈앞의 컴퓨터(계산기, 스마트폰 등등 포함)은 이와 같은 상황에 처해 있다. 

전에 뭘봤는지도 까먹고 (어떻게 구현을 한다면 될지도 모르지만) 한눈에는 안보이고 그냥 일일이 뒤져야 하는 상황이라는 뜻이다.

그대신 컴퓨터에게는 막강한 연산 능력이있다. 그것으로 정렬하는 속도를 보완해보자 하는 개념 속에 여러가지 방법이 고안 되었고, 그중 폰 노이만이 고안한 최적화 된 방법이 합병정렬(merge sort)라는 개념이다.



## 2.그래서 얼마나 빠른데 
그렇다 과거의 천재들이 고안한 방법들을 우리가 배우는 이유는 효과적이어서 일것이다.

알고리즘이 얼마나 빠른지를 측정해주는 방법은 [**빅오 표기법**](https://en.wikipedia.org/wiki/Big_O_notation)(점근 표기법-위키백과링크)이라는 표기법이다.

간단하게 설명하자면 






-----

### 다음은 우리 ChatGPT형님께서 짜준 코드이다.
```java
public class MergeSort {
    public static void mergeSort(int[] arr, int start, int end) {
        if (start < end) {
            int mid = (start + end) / 2;
            mergeSort(arr, start, mid);
            mergeSort(arr, mid + 1, end);
            merge(arr, start, mid, end);
        }
    }

    public static void merge(int[] arr, int start, int mid, int end) {
        int[] tempArr = new int[end - start + 1];
        int i = start;
        int j = mid + 1;
        int k = 0;

        while (i <= mid && j <= end) {
            if (arr[i] < arr[j]) {
                tempArr[k++] = arr[i++];
            } else {
                tempArr[k++] = arr[j++];
            }
        }

        while (i <= mid) {
            tempArr[k++] = arr[i++];
        }

        while (j <= end) {
            tempArr[k++] = arr[j++];
        }

        for (i = start; i <= end; i++) {
            arr[i] = tempArr[i - start];
        }
    }
}
```

ㄹ