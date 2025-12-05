# 11. Container With Most Water

**Difficulty:** Medium  
**Topic:** Two Pointers

## 💡 Intuition
The area is determined by the shorter line between the two pointers. To find a larger area, we must try to find a taller line.

**Strategy:** Start with the maximum width (pointers at edges). Always move the pointer that points to the **shorter** line inward.

## 🐍 Solution 1: Brute Force (Reference)
*Time Limit Exceeded* - This checks every pair. We keep this here just to remember why it's slow.

```python
def maxArea_Brute(height: List[int]) -> int:
    max_area = 0
    for i in range(len(height)):
        for j in range(i+1, len(height)):
            h = min(height[i], height[j])
            w = j - i
            area = h * w
            
            if max_area < area:
                max_area = area
    return max_area

Solution 2: Two Pointers (Optimal)
We move the shorter line inward because that is the only way to potentially find a taller line

class Solution:
    def maxArea(self, height: List[int]) -> int:
        max_area = 0
        i = 0 
        j = len(height) - 1
        
        while i < j:
            # Calculate current area
            current_h = min(height[i], height[j])
            current_w = j - i
            area = current_h * current_w
            
            # Update max if current is bigger
            if max_area < area:
                max_area = area
            
            # Move the pointer of the shorter line
            if height[i] >= height[j]:
                j = j - 1
            else:
                i = i + 1
                
        return max_area