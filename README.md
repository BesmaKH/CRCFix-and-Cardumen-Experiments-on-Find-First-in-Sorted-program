# RCFix-and-Cardumen-Experiments-on-Find-First-in-Sorted-program
This experiment is to evaluate effectiveness of two representative automatic program repair tools Cardumen and CRCFix on repairing find first in sorted program from [QuixBugs](https://github.com/jkoppel/QuixBugs/) benchmark when the program contains more than one single fault. [QuixBugs](https://github.com/jkoppel/QuixBugs/) is a benchmark suite of 40 confirmed bugs from classic algorithms with a bug on a single line of code. Particularly, Find first in sorted is a program where the goal is to find the first occurrence of a certain integer in a sorted array.

Before we start our experiment, we did some preperation work to contribute find first in sorted program with a non-deterministic specification to evaluate CRCFix and Cardumen approach. We instantiate case studies where, in each, we insert in a convenient way two single site faults in the buggy program to figure out, support or demonstrate a foundation. We also modify the test suite when needed. Find first in sorted is equipped with an original test suite of size 7.  

Our Tool RCFix was built using  [Astor](https://github.com/SpoonLabs/astor/) a famous open source program repair tool. CRCFix use the same patch generation approach as Cardumen but use Relative Correctness in  a stepwise correctness enhancement process.
# Folder Structures
Each folder corresponds to a case study, it contains:
- Find_first_sorted.java: The buggy program
- outputRCFix: The output of the RCFix approach
- outputCardumen: The output of the Cardumen approach
# Correct Find_first_in_sorted program :
this is the correct version of the program under repair:
```javascript

public class FIND_FIRST_IN_SORTED {

    public static int find_first_in_sorted(int[] arr, int x) {
      	  int lo = 0;
        	  int hi = arr.length;
                 int k=-1;

        while (lo < hi) {
           		 int mid = (lo + hi) / 2; // check if this is floor division

           		 if (x == arr[mid] && (mid == 0 || x != arr[mid-1])) {
            		    k= mid;
		    break;
           		 } else if (x <= arr[mid]) {
               		 hi = mid;
          			  } else {
     		                lo = mid + 1;
            }
        }

        return k;
    }

}

```
