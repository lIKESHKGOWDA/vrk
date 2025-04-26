1.def max_steal(val):
    n = len(val)
    if n == 0:
        return 0
    if n == 1:
        return val[0]
    
    # Create a dp array
    dp = [0] * n
    dp[0] = val[0]
    dp[1] = max(val[0], val[1])
    
    for i in range(2, n):
        dp[i] = max(val[i] + dp[i-2], dp[i-1])
    
    return dp[-1]

# Sample input
val = [6, 7, 1, 3, 8, 2, 5]
print("Maximum stolen value:", max_steal(val))
2.def print_pattern():
    pattern = [
        [1,1,1,1,2],
        [3,2,2,2,2],
        [3,3,3,3,4],
        [5,4,4,4,4],
        [5,5,5,5,6]
    ]

    for row in pattern:
        print(''.join(str(x) for x in row))

print_pattern()

3.def is_disarium(num):
    num_str = str(num)
    total = sum(int(digit) ** (idx + 1) for idx, digit in enumerate(num_str))
    return total == num

def first_n_disarium(n):
    result = []
    num = 0
    while len(result) < n:
        if is_disarium(num):
            result.append(num)
        num += 1
    return result

def disarium_between(start, end):
    return [num for num in range(start, end+1) if is_disarium(num)]

# First n Disarium numbers
n = 5
print(f"First {n} Disarium numbers:", first_n_disarium(n))

# Disarium numbers between two given numbers
start = 50
end = 200
print(f"Disarium numbers between {start} and {end}:", disarium_between(start, end))
