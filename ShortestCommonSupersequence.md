## Shortest Common Supersequence

Given two strings str1 and str2, return the shortest string that has both str1 and str2 as subsequences. If there are multiple valid strings, return any of them.

A string s is a subsequence of string t if deleting some number of characters from t (possibly 0) results in the string s.

 

**Example 1:**
```
Input: str1 = "abac", str2 = "cab"
Output: "cabac"
```
**Explanation:** 
>-str1 = "abac" is a subsequence of "cabac" because we can delete the first "c".
>-str2 = "cab" is a subsequence of "cabac" because we can delete the last "ac".
*The answer provided is the shortest such string that satisfies these properties.*

**Example 2:**
```
Input: str1 = "aaaaaaaa", str2 = "aaaaaaaa"
Output: "aaaaaaaa"
```
 

**Constraints:**

>-1 <= str1.length, str2.length <= 1000
>=str1 and str2 consist of lowercase English letters.

**Solution:**
```
class Solution {
    public static String printlcs(String first,String second )
	{
		String output[][]=new String[first.length()+1][second.length()+1];
		for(int i=0;i<=first.length();i++)
		{
			for(int j=0;j<=second.length();j++)
			{
				output[i][j]="";
			}
		}
		for(int i=first.length()-1;i>=0;i--) {
			for(int j=second.length()-1;j>=0;j--)
			{
				if(first.charAt(i)==second.charAt(j))
				{
					output[i][j]=first.charAt(i)+output[i+1][j+1];	
				}
				else
				{
					if(output[i+1][j].length()>output[i][j+1].length())
					{
						output[i][j]=output[i+1][j];
					}
					else
					{
						output[i][j]=output[i][j+1];
					}
				}
			}
		}
		return output[0][0];
	}
    public String shortestCommonSupersequence(String str1, String str2) {
        String s=printlcs(str1,str2);
        int k=0;
        int l=0;
        String total="";
        for(int i=0;i<s.length();i++)
        {
            
            while(k<str1.length() )
            {
                if(str1.charAt(k)!=s.charAt(i))
                {
                    total+=str1.charAt(k);
                    k++;
                }
                else
                {
                    k++;
                    break;
                }
                
            }
            while(l<str2.length() )
            {
                if(str2.charAt(l)!=s.charAt(i))
                { total+=str2.charAt(l);
                    l++;
                }
                else
                {
                    l++;
                    break;
                }
                
            }
            
            total+=s.charAt(i);
        }
        while(k<str1.length())
        {
            total+=str1.charAt(k);
            k++;
        }
        while(l<str2.length())
        {
            total+=str2.charAt(l);
            l++;
        }
        return total;
    }
}
```
[FOLLOW FOR MORE CONTENT](https://github.com/surajrawat1210/dailychallenge/)
