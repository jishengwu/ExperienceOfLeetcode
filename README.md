# ExperienceOfLeetcode
//this is the code of the way to get the longest common prefix of two strings
// during this process,we use two layers of loops,the first one is to control the flow of string arrays,and the second one is to control the comparison of every chars in the near two strings.
// the main faults happens when it's the case of some special ,e.g.: strs==null or strs arrays only have one element but it's null.
// int this process of dealing with this error,i thought that when we deal with the arrays or the linary date structures, the error mainly appears when the element is null,0,or the boundary elements.so in the next days,we should pay more attention to these special cases.
class Solution {
	    public String longestCommonPrefix(String[] strs) {
	        int num=strs.length;
	        if(num==0) return new String(); // to deal with the special case that strs == null
	        if(num==1) return strs[0];// to deal with the special case that strs[0]==null
	        int index=0;
	        int flag=0;
	        while(true)
	        {
	        	for(int i=0;i<num-1;i++)
	        	{
	        		flag=1;
	        		if(!Solution.compareElem(strs[i], strs[i+1], index)){
	        			flag=0;
	        			break;
	        		}
	        	}
	        	if(flag==0) break;
	        	else index++;
	        }
	        if(index>=0 && strs[0]!=null) return strs[0].substring(0, index);
	        else return new String();
	    }
      // compare the specific index of two strings,if same, return true
	    public static boolean compareElem(String str1,String str2,int index)
	    {
	    	if(str1==null || str2==null) return false;
	    	int min=str1.length()>str2.length()?str2.length():str1.length();
	    	if(index>=min) return false;
	    	else if(str1.charAt(index)==str2.charAt(index)) return true;
	    	else return false;
	    }
	}
