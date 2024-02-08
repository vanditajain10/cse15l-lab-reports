# CSE 15 L WEEK 3 LAB REPORT 

## PART 1 

## Bug:- Method static int[] reversed(int[] arr)

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

  

