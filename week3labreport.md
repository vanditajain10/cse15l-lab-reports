# CSE 15 L WEEK 3 LAB REPORT 

## PART 1 

## Bug:- Method ``` static int[] reversed(int[] arr) ```

* Failure-inducing input
  
  ```
   @Test
  public void testReversed1() {
    int[] input1 = {4,5,6};
    assertArrayEquals(new int[]{6,5,4}, ArrayExamples.reversed(input1));
  } 
```

* Non failure-inducing input

```
@Test 
public void testReversed2() {
    int[] input1 = { 3 };
    assertArrayEquals(new int[]{ 3 }, ArrayExamples.reversed(input1));
}
 ```
* The symptom
![Image](testfail.png)
* Bug before:- The bug arises in the line ``` arr[i] = newArray[arr.length - i - 1]; ``` because we are changing the values of the original array due to which we are not being able to correctly extract the value present at previous indexes.
```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
    
  }
```

* Ammended code:- I have fixed the bug by replacing the line with the bug by ``` newArray[i] = arr[arr.length - i - 1]; ``` line as well as returning the new array. Through this I am able to correctly extract the value at previous indexes and assign them to the correct indexes of the new array.
```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
  }
```

## PART 2
## Command:- ``` find ```

* **The ``` -type ``` option**
* **Source :- [https://www.redhat.com/sysadmin/linux-find-command](https://www.redhat.com/sysadmin/linux-find-command)**

**Example 1:-**
* Input:- ``` find ./911report  -type f ```
* Output :-

```
./911report/chapter-13.4.txt
./911report/chapter-13.5.txt
./911report/chapter-13.1.txt
./911report/chapter-13.2.txt
./911report/chapter-13.3.txt
./911report/chapter-3.txt
./911report/chapter-2.txt
./911report/chapter-1.txt
./911report/chapter-5.txt
./911report/chapter-6.txt
./911report/chapter-7.txt
./911report/chapter-9.txt
./911report/chapter-8.txt
./911report/preface.txt
./911report/chapter-12.txt
./911report/chapter-10.txt
./911report/chapter-11.txt

```
This command gives the path of all the files that are present in the current working directory i.e ``` /technical/911report  ```. It is helpful in order to get an idea of the files are present in our repository. It is also useful in order to get the path of a specific file in a specific directory. 

**Example 2:-**
* Input:- ``` find . -type d ```
* Output :-

```
./government
./government/About_LSC
./government/Env_Prot_Agen
./government/Alcohol_Problems
./government/Gen_Account_Office
./government/Post_Rate_Comm
./government/Media
./plos
./biomed
./911report

```
  
This command gives the path of all the directories that are present in the current working directory i.e ``` /technical ```. It is helpful in order to get an idea of the directories are present as well as how to access them.

* **The ``` -size ``` option**
* **Source:- [https://tecadmin.net/linux-find-command-with-examples/](https://tecadmin.net/linux-find-command-with-examples/)** 

**Example 1:-**
* Input:- ``` find ./plos -size +25k ```
* Output :-

```
./plos/pmed.0020059.txt
./plos/pmed.0020073.txt
./plos/pmed.0020249.txt
./plos/pmed.0020103.txt
./plos/pmed.0010028.txt
./plos/pmed.0010064.txt
./plos/pmed.0020160.txt
./plos/pmed.0010062.txt
./plos/pmed.0020162.txt
./plos/pmed.0020016.txt
./plos/pmed.0020018.txt
./plos/pmed.0020182.txt
./plos/pmed.0020246.txt
./plos/pmed.0020050.txt
./plos/pmed.0020045.txt
./plos/journal.pbio.0020439.txt
./plos/pmed.0010036.txt
./plos/pmed.0010008.txt
```
This command gives the path of all the files that are present in the current working directory i.e ``` /technical/plos``` which have size greater than 25KB. It is helpful in order to get an idea of the files that are present of a specific size.

**Example 2:-**
* Input:- ``` find ./biomed -size -10k ```
* Output :-

```
./biomed/1472-6769-1-4.txt
./biomed/1471-2490-3-2.txt
./biomed/1471-2334-3-13.txt

```
This command gives the path of all the files that are present in the current working directory i.e ``` /technical/biomed``` which have size less than 10KB. It is helpful in order to get an idea of the files that are present of a specific size. We can give the range preference too according to our own wish.

* **The ``` -name ``` option**
* **Source:- [https://tecadmin.net/linux-find-command-with-examples/](https://tecadmin.net/linux-find-command-with-examples/)**

**Example 1:-**
* Input:- ``` find ./911report -name 'chapter-8.txt' ```
* Output :-

``` ./911report/chapter-8.txt ```

This command gives the path the file which has a name of ``` chapter-8.txt ``` present in the current working directory i.e ``` /technical/911report ``` . It is helpful in order to find the path of the specific file which we might just know by name and not its path.

**Example 2:-**
* Input:- ``` find ./government/Alcohol_Problems -name '*.txt'```
* Output :-

```
./government/Alcohol_Problems/Session2-PDF.txt
./government/Alcohol_Problems/Session3-PDF.txt
./government/Alcohol_Problems/DraftRecom-PDF.txt
./government/Alcohol_Problems/Session4-PDF.txt

```
This command gives the path all the files which have an extension of .txt that present in the current working directory i.e ``` /technical/government/Alcohol_Problems ``` . It is helpful when we want to see and manipulate the extensions of different files that are present inside certain directories.

* **The ``` -mtime ``` option**
* **Source:- [https://www.geeksforgeeks.org/find-command-in-linux-with-examples/](https://www.geeksforgeeks.org/find-command-in-linux-with-examples/)**


**Example 1:-**
* Input:- ``` find ./911report -mtime -7 ```
* Output :-

```
./911report
./911report/chapter-13.4.txt
./911report/chapter-13.5.txt
./911report/chapter-13.1.txt
./911report/chapter-13.2.txt
./911report/chapter-13.3.txt
./911report/chapter-3.txt
./911report/chapter-2.txt
./911report/chapter-1.txt
./911report/chapter-5.txt
./911report/chapter-6.txt
./911report/chapter-7.txt
./911report/chapter-9.txt
./911report/chapter-8.txt
./911report/preface.txt
./911report/chapter-12.txt
./911report/chapter-10.txt
./911report/chapter-11.txt

```

This command gives the path of all the files which have been modified in the last 7 days and are present in the current working directory i.e ``` /technical/911report ``` . It is helpful in order to get an idea of all the modifications that have taken place especially when multiple people are working on the same project.


**Example 2:-**
* Input:- ``` find ./government/Env_Prot_Agen -mtime -5 ```
* Output :-

```
./government/Env_Prot_Agen
./government/Env_Prot_Agen/multi102902.txt
./government/Env_Prot_Agen/section-by-section_summary.txt
./government/Env_Prot_Agen/jeffordslieberm.txt
./government/Env_Prot_Agen/final.txt
./government/Env_Prot_Agen/ctf7-10.txt
./government/Env_Prot_Agen/ctf1-6.txt
./government/Env_Prot_Agen/ro_clear_skies_book.txt
./government/Env_Prot_Agen/ctm4-10.txt
./government/Env_Prot_Agen/1-3_meth_901.txt
./government/Env_Prot_Agen/atx1-6.txt
./government/Env_Prot_Agen/tech_sectiong.txt
./government/Env_Prot_Agen/bill.txt
./government/Env_Prot_Agen/nov1.txt
./government/Env_Prot_Agen/tech_adden.txt

```

This command gives the path of all the files which have been modified in the last 5 days and are present in the current working directory i.e ```/technical/government/Env_Prot_Agen ``` . It is helpful in order to get an idea of all the modifications that have taken place especially when multiple people are working on the same project. It is also useful when we want to check if we have accidentally modified a file in that particular directory or not 







