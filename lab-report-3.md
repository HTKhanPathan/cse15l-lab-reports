# Part 1 of report
## Bug selected:
I chose the bug in the reverseInPlace method
## Failure inducing input, JUnit test and associated code:
```
  @Test
  public void testReverseInPlaceWithMultipleElements(){
    int[] input = {1,2,3,4,5};
    ArrayExamples.reverseInPlace(input);
    assertArrayEquals(new int[]{5,4,3,2,1}, input);
  }
```
## JUnit test with successful output:
```
	@Test 
	public void testReverseInPlace() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
	}
```
## Symptom
![Image](https://github.com/HTKhanPathan/cse15l-lab-reports/blob/main/code%20output%20error.png?raw=true)
## Bug before and after fix
Before:
```
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```
After:
```
  static void reverseInPlace(int[] arr) {
    int start = 0;
    int end = arr.length - 1;
    while (start < end) {
        // Swap elements at start and end indices
        int temp = arr[start];
        arr[start] = arr[end];
        arr[end] = temp;
        // Move the start index forward and the end index backward
        start++;
        end--;
    }
  }
```

