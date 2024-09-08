def find_unique_numbers(arr):
    """Finds the two unique numbers in a given array.

    Args:
        arr: The input array.

    Returns:
        A list containing the two unique numbers in ascending order.
    """

    xor_result = 0
    for num in arr:
        xor_result ^= num

    # Find the rightmost set bit in xor_result
    rightmost_set_bit = xor_result & ~(xor_result - 1)

    # Divide the array into two groups based on the rightmost set bit
    group1 = []
    group2 = []
    for num in arr:
        if num & rightmost_set_bit:
            group1.append(num)
        else:
            group2.append(num)

    # Find the unique numbers in each group
    unique_num1 = 0
    unique_num2 = 0
    for num in group1:
        unique_num1 ^= num
    for num in group2:
        unique_num2 ^= num

    # Return the unique numbers in ascending order
    return sorted([unique_num1, unique_num2])

# Example usage:
arr = [1, 2, 3, 2, 1, 4]
result = find_unique_numbers(arr)
print(result)  # Output: [3, 4]
