# interviewbit--array--find-permutation

**------> Question:**

Given a positive integer n and a string s consisting only of letters D or I, you have to find any permutation of first n positive integer that satisfy the given input string.

D means the next number is smaller, while I means the next number is greater.

Notes

Length of given string s will always equal to n - 1
Your solution should run in linear time and space.
Example :

Input 1:

n = 3

s = ID

Return: [1, 3, 2]


------> Code:

**1st method (using stack):**

vector<int> Solution::findPerm(const string s, int n) {

    int count=0,m=s.length();
    stack<int> st;
    vector<int> v;

    for(int i=0;i<m;i++){
        count++;
        st.push(count);

        if(s[i]=='I'){
            while(!st.empty()){
                v.push_back(st.top());
                st.pop();
            }
        }
    }

    count++;
    st.push(count);

    while(!st.empty()){
        v.push_back(st.top());
        st.pop();
    }

    return v;
}
                          

**2nd method(simple):**
                          
vector<int> Solution::findPerm(const string s, int n) {

   int x=0,y=1,m=s.length();
    vector<int> v;

    for(int i=0;i<m;i++){
        x++;

        if(s[i]=='I'){
            for(int j=x;j>=y;j--){
                v.push_back(j);
            }
            y=x+1;
        }
    }

    x++;
    for(int i=x;i>=y;i--){
        v.push_back(i);
    }

    return v;

}


                          
                          
