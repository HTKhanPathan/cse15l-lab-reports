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
The original code was not swapping the places of the array correctly. Instead of it being reversed, it just made a mirror of the array: the elements after \
the midpoint were the same as the ones before. \
The change I made was a while loop that incremented the start value and decremented the end value to converge at the midpoint and break the loop. \
By using a temporary variable, the array has no repeated value so the error of the mirrored array does not occur and the reversed array matches the test case.
# Part 2: Researching grep
## Using -n
` hassankhan@HTKs-MacBook-Pro docsearch % grep -rn "DNA" ./technical/biomed/*.txt > DNAinstances.txt `
Using -rn on grep it searched the entire biomed directory's files to find all instances of "DNA". Asking ChatGPT \
"how to use grep to find all instances of DNA in ./technical/biomed/*.txt with line numbers" it gave me the above \       code saying that -r means it searches the subdirectories recursively and -n outputs the line number alongside. There \    were too many instances to show in a code block so I used > to place the output into a file called DNAinstances.txt
```
hassankhan@HTKs-MacBook-Pro docsearch % grep -n -c -r  "Introduction" ./technical/plos
./technical/plos/pmed.0020273.txt:0
./technical/plos/journal.pbio.0030032.txt:0
./technical/plos/pmed.0020065.txt:0
./technical/plos/pmed.0020071.txt:0
./technical/plos/pmed.0020059.txt:1
./technical/plos/pmed.0010039.txt:0
./technical/plos/journal.pbio.0020354.txt:0
```
-n -c and -r to find the number of lines in which "Introduction" is present
## Using -c
```
hassankhan@HTKs-MacBook-Pro docsearch % grep -c "circulation" ./technical/biomed/rr74.txt
8
```
I used `man grep` to look up the documentation. I then saw -c and proceeded to write the above command to count the occurences of "circulation" in the file
```
hassankhan@HTKs-MacBook-Pro docsearch % grep -c '^$' ./technical/biomed/rr74.txt
./technical/biomed/rr74.txt:1
```
I used -c to count the number of blank lines in the file, using ChatGPT to figure out how to do it.
## Using -H
```
hassankhan@HTKs-MacBook-Pro docsearch % grep -H "circulation" ./technical/biomed/rr74.txt
./technical/biomed/rr74.txt:        circulation in many mammals. NO has been proposed as a
./technical/biomed/rr74.txt:        circulation, and previous studies using NOS inhibitors [ 1,
./technical/biomed/rr74.txt:          pulmonary circulation following hypoxia resulted in
./technical/biomed/rr74.txt:        coronary circulation of eNOS-deficient mice, but its role
./technical/biomed/rr74.txt:        in the pulmonary circulation is unknown [ 8, 30]. However,
./technical/biomed/rr74.txt:        circulation.
./technical/biomed/rr74.txt:        circulation as suggested by Toporsian 
./technical/biomed/rr74.txt:        activity in the systemic circulation. However, those
```
I saw how -H on the man grep and asked ChatGPT how to use it effectively and then I tried it out myself first on a single file

```
hassankhan@HTKs-MacBook-Pro docsearch % grep -H "cell" ./technical/biomed/rr74.txt ./technical/biomed/rr73.txt
./technical/biomed/rr74.txt:        the redox state of pulmonary artery endothelial cells in
./technical/biomed/rr74.txt:        expression in systemic and pulmonary endothelial cells from
./technical/biomed/rr73.txt:        contraction and degraded the extracellular matrix. NE added
./technical/biomed/rr73.txt:        this increased degradation of extracellular collagen may be
./technical/biomed/rr73.txt:        extracellular matrix.
./technical/biomed/rr73.txt:        this context, fibroblasts are known to express cell surface
./technical/biomed/rr73.txt:        activity of other mediators in the extracellular milieu [
./technical/biomed/rr73.txt:        protease activity responsible for extracellular matrix
./technical/biomed/rr73.txt:        that lead to extracellular matrix degradation have the
./technical/biomed/rr73.txt:        in co-culture can release MMPs and degrade extracellular
./technical/biomed/rr73.txt:            Human fetal lung fibroblasts (cell line HFL-1),
./technical/biomed/rr73.txt:            streptomycin and 0.25 μg/ml fungizone. The cells were
./technical/biomed/rr73.txt:            between cell passages 14 and 16. Blood monocytes were
./technical/biomed/rr73.txt:            isolated from blood cells of healthy blood donors [
./technical/biomed/rr73.txt:            criteria of cell morphology on Wright stained
./technical/biomed/rr73.txt:            cellophane sheets (Pharmacia Biotech, San Francisco,
```
Then I tried it on two files
## Using -o
```
hassankhan@HTKs-MacBook-Pro docsearch % grep -o "circulation" ./technical/biomed/rr74.txt   
circulation
circulation
circulation
circulation
circulation
circulation
circulation
circulation
```
I saw the documentation of -o and wondered how it worked and tried it out to a strange and unusable result
```
hassankhan@HTKs-MacBook-Pro docsearch % grep -no "circulation" ./technical/biomed/rr74.txt
8:circulation
10:circulation
225:circulation
342:circulation
343:circulation
346:circulation
394:circulation
397:circulation
```
I then remembered how that -n shows the line number of the occurence and using it combination with -o resulted in \ 
the useless output of only -o to be actually useful
