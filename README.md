# King-s-Treasure-Hunt

In a kingdom, King Aran has n treasure chests, each filled with a different number of gold coins. He wants to examine them in groups of k chests at a time. For each group, he needs to find the chest with the most coins and add that value to his total wealth. Can you help the king calculate the total wealth from all the groups?


from collections import deque

def max_sum_of_windows(n, k, arr):
    total_wealth = 0
    dq = deque()  

    for i in range(n):
        if dq and dq[0] < i - k + 1:
            dq.popleft()

        while dq and arr[dq[-1]] <= arr[i]:
            dq.pop()

        dq.append(i)

        if i >= k - 1:
            total_wealth += arr[dq[0]]  

    return total_wealth

n, k = map(int, input().split())
arr = list(map(int, input().split()))

print(max_sum_of_windows(n, k, arr))
