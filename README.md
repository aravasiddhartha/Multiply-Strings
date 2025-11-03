class Solution(object):
    def multiply(self, num1, num2):
        """
        :type num1: str
        :type num2: str
        :rtype: str
        """
        if num1 == "0" or num2 == "0":
            return "0"

        # Initialize result array of zeros (max possible length = len(num1) + len(num2))
        res = [0] * (len(num1) + len(num2))

        # Reverse both numbers for easier calculation (start from least significant digit)
        num1, num2 = num1[::-1], num2[::-1]

        # Multiply each digit
        for i in range(len(num1)):
            for j in range(len(num2)):
                digit1 = ord(num1[i]) - ord('0')
                digit2 = ord(num2[j]) - ord('0')
                res[i + j] += digit1 * digit2
                # Handle carry immediately
                res[i + j + 1] += res[i + j] // 10
                res[i + j] %= 10

        # Remove leading zeros if any
        while len(res) > 1 and res[-1] == 0:
            res.pop()

        # Convert back to string and reverse
        return ''.join(map(str, res[::-1]))
        
