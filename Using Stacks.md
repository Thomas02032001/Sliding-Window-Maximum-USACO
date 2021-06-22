#Using Stacks And Next Greater Concept : -

So we have been solved this problem in sliding window technic, deque and many more ways to solve this problem
but now we are going to solve this one with the help of stacks

//**************************************************************************

 vector<int> maxSlidingWindow(vector<int>& v, int k) {
        
        vector<int>g,a;
        int n=v.size(),i,j;
        stack<pair<int,int>>s;
        
        for(i=0; i<n; i++){
            g.push_back(INT_MAX);
        }
        
        for(i=0; i<n; i++){
            if(s.empty()){
                s.push({v[i],i});
            }else{
                while(!s.empty() && v[i]>=s.top().first){
                    g[s.top().second] = i;
                    s.pop();
                }
                s.push({v[i],i});
            }
        }
        j=0;
        for(i=0; i<=n-k; i++){
            if(j<i)
                j=i;
            while( (g[j]) < (k+i) ){
                j = g[j];
            }
            a.push_back(v[j]);
        }
        return a;
    }
    
 //***********************************************************
 
 At Stage one we are finding the next immediate greater element of the present element and storing in
 the vector "g" 
 
 Later we are traversing the vector upto (v.size()-k) and repeating the while loop
 and finding the max element...
