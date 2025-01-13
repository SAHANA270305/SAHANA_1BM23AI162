# SAHANA_1BM23AI162
hacker rank challenge solutions


1) BALANCED BRACKETS:

import math

import os

import random

import re

import sys


def isbalanced(s):

    stack = []
    
    matching_bracket = {')': '(', '}': '{', ']': '['}
    
    for A in s:
        if A in matching_bracket.values():
            stack.append(A)
        elif A in matching_bracket:
            if stack and stack[-1] == matching_bracket[A]:
                stack.pop()
            else:
                return "NO"
    

    return "YES" if not stack else "NO"


n = int(input())  
for _ in range(n):

    s = input().strip()  
    print(isbalanced(s))

    
2) QUEUE USING TWO STACKS:

class QueueUsingTwoStacks:

    def __init__(self):
        self.in_stack = [] 
        self.out_stack = []  
    
    def enqueue(self, x):
       
        self.in_stack.append(x)
    
    def dequeue(self):
        
        if not self.out_stack:
            while self.in_stack:
                self.out_stack.append(self.in_stack.pop())
        
        if self.out_stack:
            return self.out_stack.pop()
        return None  
    
    def print_front(self):
        
        if not self.out_stack:
            while self.in_stack:
                self.out_stack.append(self.in_stack.pop())
        
        if self.out_stack:
            return self.out_stack[-1]
        return None  

def process_queries(queries):

    queue = QueueUsingTwoStacks()
    
    for query in queries:
        parts = query.split()
        type_of_query = int(parts[0])
        
        if type_of_query == 1:
            
            x = int(parts[1])
            queue.enqueue(x)
        elif type_of_query == 2:
           
            queue.dequeue()
        elif type_of_query == 3:
            
            print(queue.print_front())


if __name__ == "__main__":
   
    q = int(input().strip())
    
   
    queries = []
    for _ in range(q):
        queries.append(input().strip())
    
    
    process_queries(queries)


3) GAME OF TWO STACKS:

import math

import os

import random

import re

import sys


def twoStacks(maxsum, a, b):
    
    n, m = len(a), len(b)
    i, j = 0, 0
    current_sum = 0
    max_score = 0
    
   
    while i < n and current_sum + a[i] <= maxsum:
        current_sum += a[i]
        i += 1
    
    max_score = i  
    
    
    while j < m:
        current_sum += b[j]
        j += 1
        
        
        while current_sum > maxsum and i > 0:
            i -= 1
            current_sum -= a[i]
        
        
        if current_sum <= maxsum:
            max_score = max(max_score, i + j)
    
    return max_score


def main():

    t = int(input())
    for _ in range(t):
        
        n, m, maxsum = map(int, input().split())
        x = list(map(int, input().split())) 
        y = list(map(int, input().split())) 
        
        
        result = twoStacks(maxsum, x, y)
        print(result)


if __name__ == "__main__":

    main()





