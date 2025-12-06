class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:

        if len(s)<=1:
            return len(s)

        left=0
        longest_list=set()
        longest_seq=0
       
        for right in range(len(s)):
            if  s[right]  in longest_list:
                while s[right] in longest_list:
                    longest_list.remove(s[left])
                    left=left+1
            longest_list.add(s[right])
            longest_seq=max(longest_seq,len(longest_list) )   
        return longest_seq
            


        