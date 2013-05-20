---
layout: post
title: "Introduction to Recursion"
---

###1. Definition:
   Any function that calls itself (directly or indirectly) is recursive. 
      
      
###2. Understanding Recursion    

####2.1 When to use
Usually for tasks that can be defined in terms of similar subtasks.  

A good hint that a problem is recursive is that it appears to be built off sub-problems  

For example:  traversal problems often have recursive solutions  
    
    
####2.2 Two components of recursion
* base case: the function stop recurse.
* recursive case: the function calls itself to perform a subtask.  
 
#####Note:   
If a recursion function does never reach it's base case,it will recurse infinite. lead to stack overflow.eventually the program crashes.
      
   
####2.3 Recursion vs Iteration
First of all,any problem can be solved recursely can also be solved iterately.  
  
* recursion solution is simpler to understand and often need less code than iteration.
* iteration is more efficient.due to recursion solution has large overhead for function calls.
      
   

###3. Example 
####3.1 Question: return all subsets of a set

######Thinking :
Divide the big set into two parts, set = first item + smallset.if we can get all subsets of the smallset.then we can easily get all subsets.so we can use recursion to solve the problem.  
                                                 

######Coding:
        void GetSubsets( Type * set, int numofset,int k, vector< vector< Type > > & allsubsets ) {
            if( k == numofset - 1 )
                //base case
                //process the last element in the set
                allsubsets.push_back( new vecotr< Type >( set[ k ] ) );
            else {
                //recursive case
                
                //get smallsubsets
                GetSubsets( set, numofset, k+1, allsubsets );
                
                //using current item and smallsubsets to get allsubsets
                Type item = set[ k ];
                
                //process presubsets:insert current item into every set (first place of every set) in smallsubsets
               
                vector< vector< Type > > presubsets = allsubsets;
                vector< Type >::iterator ite1;
                vector< vector< Type > >::iterator ite2;
                
                for( ite2 = presubsets.begin(); ite2 != presubsets.end(); ite2++ ){
                    ite1 = ite2 -> begin();
                    ite2 ->insert( ite1, item );
                }
                
                //add current item into allsubsets
                allsubsets.push_back( new vector< Type >( item ) );
               
               //add processed presubsets into allsubsets
                allsubsets.insert( allsubsets.end(), presubsets.begin(), presubsets.end() );
            }    
        }




