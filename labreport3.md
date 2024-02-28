# Lab Report 3

## Part 1 - Bugs 
### A failure-inducing input for the buggy program

Input: `{1, 2, 3, 4, 5, 6}`

JUnit Test Code for `testReverseInPlace2`: 
```
@Test 
public void testReverseInPlace2() {
  int[] input1 = { 1, 2, 3, 4, 5, 6 };
  ArrayExamples.reverseInPlace(input1);
  assertArrayEquals(new int[]{ 6, 5, 4, 3, 2, 1 }, input1);
}
```
Buggy Method Implementation: 
```
static void reverseInPlace(int[] arr) {
  for(int i = 0; i < arr.length; i += 1) {
    arr[i] = arr[arr.length - i - 1];
  }
}
```

JUnit Output: 
```
JUnit version 4.13.2
.E..
Time: 0.005
There was 1 failure:
1) testReverseInPlace2(ArrayTests)
arrays first differed at element [3]; expected:<3> but was:<4>
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:78)
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:28)
        at org.junit.Assert.internalArrayEquals(Assert.java:534)
        at org.junit.Assert.assertArrayEquals(Assert.java:418)
        at org.junit.Assert.assertArrayEquals(Assert.java:429)
        at ArrayTests.testReverseInPlace2(ArrayTests.java:16)
        ... 30 trimmed
Caused by: java.lang.AssertionError: expected:<3> but was:<4>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at org.junit.internal.ExactComparisonCriteria.assertElementsEqual(ExactComparisonCriteria.java:8)
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:76)
        ... 36 more

FAILURES!!!
Tests run: 1,  Failures: 1
```

### An input that doesn't induce a failure

Input: `{ 3 }`

JUnit Test Code for `testReverseInPlace`:
```
@Test 
public void testReverseInPlace() {
  int[] input1 = { 3 };
  ArrayExamples.reverseInPlace(input1);
  assertArrayEquals(new int[]{ 3 }, input1);
}
```

JUnit Output: 
```
JUnit version 4.13.2
..
Time: 0.004

OK (1 test)
```

### The symptom, as the output of running the tests 

JUnit Test Code for `testReverseInPlace` and `testReverseInPlace2`:
```
public class ArrayTests {
  @Test 
  public void testReverseInPlace() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
  }

  @Test
  public void testReverseInPlace2() {
    int[] input1 = { 1, 2, 3, 4, 5, 6 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 6, 5, 4, 3, 2, 1 }, input1);
  }
}
```

JUnit Output: 
![Image](lab3part1.png)

### The bug, as the before-and-after code change required to fix it 
Before code change required to fix it: 
```
static void reverseInPlace(int[] arr) {
  for(int i = 0; i < arr.length; i += 1) {
    arr[i] = arr[arr.length - i - 1];
  }
}
```

After code change required to fix it: 
```
static void reverseInPlace(int[] arr) {
  for(int i = 0; i < arr.length/2; i += 1) {
    int temp = arr[i];
    arr[i] = arr[arr.length - i - 1];
    arr[arr.length - i - 1] = temp;
  }
}
```

### Why the fix addresses the issue? 
In the former method implementation, the method would successfully reverse the first half of the list. However, after the first half, it would create a palindrome within the array since it would be recieving its data from the updated list, which is updating chronilogically in the list after every iteration in the loop. Therefore, this issue needs to be fixed by updating the values in the beginning and end of the list at the same time. In order to do so, we can create a local variable that will store the value of the index we are about to change and afterwords we will update the first and last element in the array and iterate till we get to the middle to successfully reverse the elements in the array. 

## Part 2 - Researching Commands (`find`)

The `find` command has many options that users can use to filter directories which users can mix and match to find their desired files. Below are 4 different ways users can effectively use the `find` command. 

### `-type c`
By using the format `find [starting_directory] -type [c]` to search through directores, the command allows the user to search for specific file types. The user is able to chose their `[starting_directory]` to start from and the `[c]` allows the user to specify the file type (such as `d` for directories or `f` for regular files).

## Example 1
```
dgupta@Dhruvs-MacBook-Pro written_2 % find ./technical -type d
./technical
./technical/government
./technical/government/About_LSC
./technical/government/Env_Prot_Agen
./technical/government/Alcohol_Problems
./technical/government/Gen_Account_Office
./technical/government/Post_Rate_Comm
./technical/government/Media
./technical/plos
./technical/biomed
./technical/911report
```

### `-size n`

By using the format `find [starting_directory] -type f -size [±][size][c]` to search through the directories, the command allows the user to decide which `[starting_directory]` to searching from, the `[±]` indicates whether it will be a greater than or less than comparsion, `[size]` specifies the size threshold, and `[c]` specifies the unit of measurement (such as `M` for megabytes, `G` for gigabytes, or `k` for kilobytes). Additionally, `-type f -size` specifies that we are searching for regular files with a specific size criteria. 

## Example 1
```
dgupta@Dhruvs-MacBook-Pro written_2 % find ./technical -type f -size +10M
./technical/government/About_LSC/commission_report-hepple.xml
./technical/government/Env_Prot_Agen/tech_adden-hepple.xml
./technical/government/Env_Prot_Agen/multi102902-hepple.xml
./technical/government/Env_Prot_Agen/bill-hepple.xml
./technical/government/Gen_Account_Office/d01591sp-hepple.xml
./technical/government/Gen_Account_Office/GovernmentAuditingStandards_yb2002ed-hepple.xml
./technical/government/Gen_Account_Office/pe1019-hepple.xml
./technical/government/Gen_Account_Office/Statements_Feb28-1997_volume-hepple.xml
./technical/911report/chapter-13.5-hepple.xml
./technical/911report/chapter-3-hepple.xml
./technical/911report/chapter-13.4-hepple.xml
```
In this example, we can see how the command allowed us to find files within the `./technical` directory that are greater than 10 megabytes. This is useful in finding large files and managing disk space. 

## Example 2
```
dgupta@Dhruvs-MacBook-Pro written_2 % find ./technical -type f -size -1k
./technical/plos/pmed.0020191.txt
./technical/plos/pmed.0020226.txt
```
In this example, we can see how the command allowed us to find files within the `./technical` directory that are less than 1 kilobyte. This is useful in finding small files that are redundant and don't have much need or use. 

### `-maxdepth n`

By using the format `find [starting_directory] -maxdepth [n]` to search through the directories, the command allows the user to decide which `[starting_directory]` to searching from and the `[n]` specifies the maximum depth of the search in the search directory. 

### Example 1
```
dgupta@Dhruvs-MacBook-Pro written_2 % find ./technical -maxdepth 1 
./technical
./technical/government
./technical/plos
./technical/biomed
./technical/911report
```
In this example, we can how the command allows us to view all of the files within the `./technical` that have a max depth of 1. This is useful for focusing on immediate contents and efficient searching. 

### Example 2
```
dgupta@Dhruvs-MacBook-Pro written_2 % find ./technical -type f -size +10M -maxdepth 2 
./technical/911report/chapter-13.5-hepple.xml
./technical/911report/chapter-3-hepple.xml
./technical/911report/chapter-13.4-hepple.xml
```
In this example, we can how the command can be used with other find commands to filter the files in the `./technical` directory that are regular files, have a size greater than 10 megabytes, and at a max depth of 2. This is useful for filtering results to find really specific files that would take too much time to manually look for. 

### `-mindepth n`

By using the format `find [starting_directory] -mindepth [n]` to search through the directories, the command allows the user to decide which `[starting_directory]` to searching from and the `[n]` specifies the minimum depth of the search in the search directory. 

### Example 1
```
dgupta@Dhruvs-MacBook-Pro written_2 % find ./technical -type d -mindepth 2
./technical/government/About_LSC
./technical/government/Env_Prot_Agen
./technical/government/Alcohol_Problems
./technical/government/Gen_Account_Office
./technical/government/Post_Rate_Comm
./technical/government/Media
```
In this example, we can how the command allows us to view all of the directories within the `./technical` that have a min depth of 2. This is useful for finding how deep the subdirectories go. 

### Example 2
```
dgupta@Dhruvs-MacBook-Pro written_2 % find ./technical -type f -maxdepth 4 -size +10M -mindepth 2
./technical/government/About_LSC/commission_report-hepple.xml
./technical/government/Env_Prot_Agen/tech_adden-hepple.xml
./technical/government/Env_Prot_Agen/multi102902-hepple.xml
./technical/government/Env_Prot_Agen/bill-hepple.xml
./technical/government/Gen_Account_Office/d01591sp-hepple.xml
./technical/government/Gen_Account_Office/GovernmentAuditingStandards_yb2002ed-hepple.xml
./technical/government/Gen_Account_Office/pe1019-hepple.xml
./technical/government/Gen_Account_Office/Statements_Feb28-1997_volume-hepple.xml
./technical/911report/chapter-13.5-hepple.xml
./technical/911report/chapter-3-hepple.xml
./technical/911report/chapter-13.4-hepple.xml
```
In this example, we can how the command can be used with other find commands to filter the files in the `./technical` directory that are regular files, have a size greater than 10 megabytes, have a max depth of 4, and a min depth of 2. This is useful for filtering results to find really specific files that would take too much time to manually look for. This specific case is useful for evaluating file managment. 






