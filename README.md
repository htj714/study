# study
学习

text1：
class Solution {
public:
   int pivotIndex(vector<int>& nums) {
        for( int i = 0; i < size(nums); i++){
            int A=0,B=0;
            for( int a = 0;  a < i; a++)
                A+=nums[a];
            for(int b = i+1; b < size(nums); b++)
                B+=nums[b];
            if( A == B)
                return i;
        }
        return -1;
    }
};
输入
[1,7,3,6,5,6]
输出
3
预期结果
3



text2:
class Solution {
public:
    int searchInsert(vector<int>& nums, int target) {
        for(int i=0;i<nums.size();i++){
            if(nums[i]>=target)
                return i;
                }
    return nums.size(); 
    }
};
输入
[1,3,5,6]
5
输出
2
预期结果
2
  
text3
struct node{
	int a, b;
};
 
bool cmp(node n1,node n2){
	return n1.a < n2.a;
}
 
class Solution {
public:
	vector<vector<int>> merge(vector<vector<int>>& intervals) {		
		for (auto it = intervals.begin(); it != intervals.end(); ){
			if ((*it).size()<2 || (*it)[0] > (*it)[1])intervals.erase(it);
			else it++;
		}
		vector<vector<int>>ans;
		int size = intervals.size();
		if (intervals.empty())return ans;
		node *p = new node[size];
		for (int k = 0; k < size; k++){
			p[k].a = intervals[k][0], p[k].b = intervals[k][1];
		}
		sort(p, p + size, cmp);
		vector<int>tmp;
		for (int k = 0; k < size;){
			tmp.clear();
			tmp.insert(tmp.end(), p[k].a);
			tmp.insert(tmp.end(), p[k].b);
			k++;
			while (k < size){
				if (p[k].a <= tmp[1]){
					tmp[1] = max(tmp[1],p[k].b);
					k++;
				}
				else{
					break;
				}
			}
			ans.insert(ans.end(), tmp);
		}
		return ans;
	}
};
 
 
 
text5
class Solution {
public:
    void rotate(vector<vector<int>>& matrix) {
        int len=matrix.size();
        //对角线互换 
        for(int i=0;i<len;i++){
    		for(int j=i+1;j<len;j++){
    			//swap(matrix[i][j], matrix[j][i]);//借助了额外的内存
				 matrix[i][j] += matrix[j][i];
				 matrix[j][i] = matrix[i][j] - matrix[j][i];
				 matrix[i][j] = matrix[i][j] - matrix[j][i];
			}
		}
		//左右颠倒
		for(int i=0;i<len;i++){
			for(int j=0;j<len/2;j++){
				//swap(matrix[i][j], matrix[i][len-j-1]);//借助了额外的内存
				matrix[i][j] = matrix[i][j] ^ matrix[i][len-j-1];
				matrix[i][len-j-1] = matrix[i][j] ^ matrix[i][len-j-1];
				matrix[i][j] = matrix[i][j] ^ matrix[i][len-j-1];
			}
		} 
    }
};
	
	
文本6：
class Clearer {
public:
    vector<vector<int> > clearZero(vector<vector<int> > mat, int n) {
        // write code here
        vector<vector<int> > matT(n);
        for(int i = 0; i < n; i++)
        {
            matT[i].resize(n);
        }
        
        for(int i = 0; i < n; i++)
        {
            for(int j = 0; j < n; j++)
            {
                if(mat[i][j] == 0)
                {
                    //如果出现了零，给标记矩阵做标记
                    for(int k = 0; k < n; k++)
                    {
                        //行
                        matT[i][k] = 1;
                        //列
                        matT[k][j] = 1;
                    }
                }
            }
        }
        
        //清零
        for(int i = 0; i < n; i++)
        {
            for(int j = 0; j < n; j++)
            {
                if(matT[i][j] == 1)
                {
                    mat[i][j] = 0;
                }
            }
        }
        return mat;
    }
};

文本7：
