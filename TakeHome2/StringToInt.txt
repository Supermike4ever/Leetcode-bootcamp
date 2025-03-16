class Solution:
    def myAtoi(self, s: str) -> int:
        sign = 1
        result = 0
        index = 0
        n = len(s)
        INT_MAX = pow(2, 31) - 1
        INT_MIN = -pow(2, 31)

        #check the sign and remove whitespace
        while index < n and s[index] == ' ':
            index+=1

        if index < n and s[index] == "+":
            sign = 1
            index+=1
        elif index < n and s[index] == "-":
            sign=-1
            index+=1
        #clear the 0s
        while index < n and s[index] == '0':
            index+=1
        
        while index < n and s[index].isdigit():
            
            digit = int(s[index])
            result = result*10 + digit
            if sign == 1 and result*1 > INT_MAX:
                return INT_MAX
            elif sign == -1 and result*-1 < INT_MIN:
                return INT_MIN
            index+=1
        
        return result*sign


