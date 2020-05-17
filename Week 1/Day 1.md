## Week 1 (May 16, 2020 - May 23, 2020)

### Day 1 - May 16, 2020: Counting Sort
### Algorithm

Technical coding interview are hard. Unless you bootstrapped with Mathematics in highschool or just born with comprehensive analytical skill, it probably take you lots of hard-working hour to truly master the subject and be confident going in interview.

In order to prepare myself for the upcoming round of coding interview in Fall Semester( around August-October 2020), I am planning to blog about my journey of learning Data Structures and Algorithms in depth and maybe use it as reference for future inquiry.

I was not familiar with [counting sort]("https://medium.com/basecs/counting-linearly-with-counting-sort-cd8516ae09b3") before, therefore I decided to take a quick deep dive into the sorting algorithm today. After learning and playaround with counting sort. Here is a overview of this sorting algorithm and what makes it special:
> 1. It applies only on integers
> 2. It sorting algorithm assumes that you know the range of your input (the integers you are trying to sort)
> 3. Works best if the range is not to wide; meaning the range is less than the number that we are trying to sort

### Algorithm process

So there is 3 parts of the algorithms.

1. In first step, we have to have a array/list that keep track of the frequency of each number in the input array.

```python
def counting_sort(minVal, maxVal, arr):
    # frequency table
    tally = [0] * (maxVal - minVal + 1)  
```

2. Second step is traversing the array and tally the frequency of each number

```python
def counting_sort(minVal, maxVal, arr):
    # frequency table
    tally = [0] * (maxVal - minVal + 1)  

    #traverse and keep increase the frequency of each number
    for num in arr:
      tally[num - minVal]+= 1 
```

3.Finally, traverse through the array and sort in-place based on the frequency of each number

Final Code: 

```python
def counting_sort(minVal, maxVal, arr):
    # frequency table
    tally = [0] * (maxVal - minVal + 1)  

    #traverse and keep increase the frequency of each number
    for num in arr:
      tally[num - minVal]+= 1
      
    #sort the input arr in-place by updating each element based on the tally array.
    i = 0 
    for index, frequency in enumerate(tally):
      number = index + minVal
      while frequency > 0:
        arr[i] = number
        i += 1
        frequency -= 1
    return arr
```




