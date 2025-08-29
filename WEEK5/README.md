# Week 5 - Arrays  2 - questions and solutions




## Maximum rooms booked
- Idea here is to use the concept of `difference array`
- We pre process the intervals and build an array `pre`.
- Then we do a running sum and store the same result.
- Then we find maximum value in `pre`  which gives us the *maximum overlapping interval*  .

```
def hotelReservations(reservation):
    p1 = reservation.split('|')
    q = [list(map(int,num.split(','))) for num in p1]
    
    #print(p1)
    #print(q)
    
    maxi = 0
    for a,b in q:
        maxi = max(maxi,a,b)
    #print(maxi)
    
    #pre-processing
    pre = [0]*(maxi+2)
    for start,end in q:
        pre[start]+=1
        pre[end+1]-=1
    
    #print(pre)
    #process the running sum
    curr = 0
    for i in range(len(pre)):
        curr += pre[i]
        pre[i] = curr
        
    
    #print(pre)
    return max(pre)
    
reservation = "1,3|2,4|3,5"
print(hotelReservations(reservation))
```

## Trek with Bear Grylls

- My thought process here is to simply remove the duplicates to make it simpler problem and proceed with the problem.
  
```
def countIt(nums,n):
        count = 0
        arr = []
        for i in range(len(nums)):
            if arr:
                if arr[-1]!=nums[i]:
                    arr.append(nums[i])
            else:
                arr.append(nums[i])
        #print(arr)
        for i in range(1,len(arr)-1):
            if arr[i-1]<arr[i]>arr[i+1] or arr[i-1]>arr[i]<arr[i+1]:
                #print(i)
                count += 1
        return count
```
