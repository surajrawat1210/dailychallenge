## 583. Delete Operation for Two Strings

Given two strings word1 and word2, return the minimum number of steps required to make word1 and word2 the same.

In one step, you can delete exactly one character in either string.

 

**Example 1:**
```
Input: word1 = "sea", word2 = "eat"
Output: 2
```
>Explanation: You need one step to make "sea" to "ea" and another step to make "eat" to "ea".

**Example 2:**

```
Input: word1 = "leetcode", word2 = "etco"
Output: 4
```
 

**Constraints:**

- 1 <= word1.length, word2.length <= 500
- word1 and word2 consist of only lowercase English letters.

**Solutions:**
```
class Solution {

    public int minDistance(String word1, String word2)
    {  
    int output[][]=new int[word1.length()+1][word2.length()+1];
    int k=1;
    for(int i=word2.length()-1;i>=0;i--,k++)
    {
        output[word1.length()][i]=k;
    }
    int l=1;
    for(int j=word1.length()-1;j>=0;j--,l++)
    {
        output[j][word2.length()]=l;
    }
    for(int i=word1.length()-1;i>=0;i--)
    {
        for(int j=word2.length()-1;j>=0;j--)
        {
            if(word1.charAt(i)==word2.charAt(j))
            {
                output[i][j]=output[i+1][j+1];
            }
            else
            {
                output[i][j]=1+Math.min(output[i][j+1],output[i+1][j]);
            }
        }
    }
        return output[0][0];
    }
}
```
