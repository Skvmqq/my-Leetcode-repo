
class Solution:
    def maxProfit(self, prices):
        #brute force--time limit Exceeded
        #O(n^2)- Time Complexity
        
        '''max_profit=0
        for i in range(len(prices)):
            for j in range((i+1),len(prices)):
                if prices[i]<prices[j]:
                    profit=prices[j]-prices[i]
                    max_profit=max(max_profit,profit)
        return max_profit'''
        
        #O(n)-Time Complexity
        max_profit=0
        left=0
        right=left+1
        while (right<len(prices)):
            if prices[left]<prices[right]:
                profit=prices[right]-prices[left]
                max_profit=max(max_profit,profit)
            else:
                left =right
            right=right+1
        return max_profit
prices=[7,1,5,3,6,4]
sol=Solution()
max_profit=sol.maxProfit(prices)
print(max_profit)



             
            
            






        
        