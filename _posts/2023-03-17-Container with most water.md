---
layout: post
title: Resolução do problema "Container With Most Water"
categories: leetcode
tags: [c++, leetcode]
author: 
- Juan
---

# Container With Most Water (Leetcode)

<p> You are given an integer array height of length n. There are n vertical lines drawn such that the two endpoints of the ith line are (i, 0) and (i, height[i]). <br>
Find two lines that together with the x-axis form a container, such that the container contains the most water. <br>
Return the maximum amount of water a container can store. <br>
Notice that you may not slant the container. </p>

![Example 1](/assets/images/question_11.jpg)

Example 1: <br>
Input: height = [1,8,6,2,5,4,8,3,7] <br>
Output: 49 <br>
Explanation: The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain is 49.

Example 2:

Input: height[1,1]

Output: 1


Constraints: 

    - n == height.length
    - 2 <= n <= 105
    - 0 <= height[i] <= 104


Para acessar o problema diretamente na plataforma Leetcode clique na [Descrição do problema](https://leetcode.com/problems/container-with-most-water/description/).


## Resolução
Neste tópico irei mostrar como resolvi este problema. 
Para resolver este problema utilizei dois ponteiros. Um apontando para o início do vetor e outro apontando para o final do vetor.
O problema pede qual é a área máxima que consegue fazer com determinadas linhas desenhadas.
O incremento ou decremento do ponteiro ocorre após a verificação de qual valor é maior.



Código:
```cpp

class Solution {
public:
    int maxArea(vector<int>& height) {
        int len = height.size();
        int start = 0;
        int end = len-1;
        int res = -1;
        int area = 0;

        while(start != end){
            area = min(height[start],height[end]) * (end-start);
            res = max(res, area);
    
            if (height[start] < height[end] && start != end){
                start++; 
            } else {
                end--; 
            }
        }

        return res;
    }
};
```

