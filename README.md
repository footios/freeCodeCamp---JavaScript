# freeCodeCamp  Challenges <a name="goUp"/>
Here are my solutions to the challenges. They are not the best, but they show my progression. 
Spool up the FTL drive!

* [Basic Algorithm Scripting](#basicAlgo)
    * [Reverse string](#reverseString)
    * [Return Largest Numbers in Arrays](#returnL)
    * [Confirm Ending](#confirmE)
    * [Repeat a String Repeat a String](#repeatS)
    * [Truncate a String](#truncateS) 
    * [Finders Keepers](#findK)
    * [Check for boolean](#checkBoolean)
    * [Title Case a Sentence](#titleCase)
    * [Slice and Splice](#sliceSplice)
    * [Falsy Bouncer](#falsyBouncer)
    * [Where do I belong](#whereBelong)
    * [Mutations](#mutations)
    * [Chunky Monkey](#chunkyMonkey)
    



# <a name="reverseString"/> Reverse String

```
  function reverseString(str) {

      let arr = []
      console.log(str.length);
      for (var i = str.length; i >= 0; i--) {
        arr.push(str[i])
        //console.log(arr);
      }
      return arr.join("");
    }
    console.log(reverseString("hello"));
```

```
//I came up with this one with the help of the hinds
  function reverseString(str) {

      let arr = [];
      arr = str.split('');
      arr.reverse();
      str = arr.join('');
      return str;
      //or just
      // return str.split('').reverse().join('');

    }
    console.log(reverseString("Greetings from Earth"));
```
FCC Solutions

```
function reverseString(str) {
  return str.split('').reverse().join('');
}
```

# <a name="basicAlgo"/> Basic Algorithm Scripting

## <a name="returnL"/> Return Largest Numbers in Arrays
* Return an array consisting of the largest number from each provided sub-array. 
```
// I didn't get the question right.
// The function should return an array with the largest numbers
// of each subarray.
// This one returns the subarray
// that has the largest number.
    function largestOfFour(arr) {
      // You can do this!
      let max = 0;
      let newArr = [];
      for (var i = 0; i < arr.length; i++) {
        for (var j = 0; j < arr[i].length; j++) {
          //  console.log(arr[i][j]);
          if (arr[i][j] > max) {
            max = arr[i][j];
            //  console.log('max ', max);
          }
          if (arr[i][j] === max)
            //  console.log('arr...', arr[i][j]);
            newArr = arr[i];
          //  console.log('newArr ', newArr);

        }
      }

      return newArr;
    }

    console.log('result ', largestOfFour(
      [
        [4, 9, 1, 3],
        [13, 35, 18, 26],
        [32, 35, 97, 39],
        [1000000, 1001, 857, 1]
      ]));
  </script>
```

## Return Largest Numbers in Arrays
Return an array consisting of the largest number from each provided sub-array.
```
  //Now it's working, but I show the solution
    // and the main mistake 
    // was the position of
    // sub2.push(max);
    function largestOfFour(arr) {
      // You can do this!
      // You can do this!
      var i, j, max = 0;
      var maxArr = [];
      for (i = 0; i < arr.length; i++) {
        console.log('i ', i); // see when this loop stars

        /* The second for loop, iterates over the first
         sub array ([4, 9, 11, 3]), gets the max number
         (like, first 4 and then 9 and then 11) and then jumbs
       back to the first for loop. But just before it starts
       iterating it pushes the last max num to maxArr.
       And so on.

       If we had the maxArr.push(max); line inside the
       second for loop, we would push every max number
       we would get. That's why we put just outside it.

        So the second for loop iterates
       over the first sub array and then jumbs back to first
       for loop, and starts iterating over the second
       sub array. That happens because it's inside the first for loop.
       That means that when i gets a value, then the second
       for loop gives us all the values for that i.length.

       Note! The funny thing here is that the second for loop
       works the same even if we do arr.lenght instead
       of arr[i].length. I don't know why.*/

        for (var j = 0; j < arr[i].length; j++) {
          if (arr[i][j] > max) {
            max = arr[i][j];
            console.log('max0 ', max);
          }
          console.log('max1 ', max);
        }
        console.log('max2 ', max);
        maxArr.push(max);
      }
      return maxArr;
    }

    console.log('result ', largestOfFour(
      [
        [4, 9, 11, 3],
        [13, 35, 18, 26],
        [32, 100, 97, 39],
        [1000000, 1002221, 857, 1]
      ]));
```

```
// FCC solution
    // Intermediate Code Solution:
    //(Declarative approach)
    /* As we see the 'map' fun first groups all the
    subarrays. Then the 'reduce' checks which number
    is larger and returns the largest one.
    And because map returns an array, the returned
    value is an array.
    */
    function largestOfFour(arr) {
      return arr.map(function(group) {
        //  console.log(group);
        return group.reduce(function(prev, current) {
          //console.log('p ', prev, 'c ', current);
          return (current > prev) ? current : prev;
        });
      });
    }


    console.log('result ', largestOfFour(
      [
        [4, 9, 1, 3],
        [13, 35, 18, 26],
        [32, 35, 97, 39],
        [1000000, 1001, 857, 1]
      ]));

```

```
    // FCC solution
    //  Advanced Code Solution:
    //  (Declarative approach)

    /*
    First we iterate over the array of arrays with the map function.
    Then we need a fun to apply it to every element of the map
    that gives us the max num.
    The Math.max does not take an array as input.
    But the apply() does.
    Math.max.apply(null, [9, 43, 20, 6])
    Note! With apply you can provide a context
    to work on, which will be the value of 'this'.
    But here we don't need a context, so we use null.
    Another thing with apply, is that it doesn't return an array,
    that's why Math.max accepts apply's output.
    So, with the apply method
    we get the elements from the map fun and then
    we 'bind' these elements to the Math.max, which returns
    the max number to the map fun, which then returns
    the array with all the max numbers.
    */
    function largestOfFour(arr) {
      return arr.map(Function.apply.bind(Math.max, null));
    }
    console.log('result ', largestOfFour(
      [
        [4, 9, 1, 3],
        [13, 35, 18, 26],
        [32, 35, 97, 39],
        [1000000, 1001, 857, 1]
      ]));
 ```
## <a name="confirmE"/>Confirm the Ending
Check if a string (first argument, str) ends with the given target string (second argument, target).
```
  // WE DID IT!!!!!!!!!
    // I did got a hind to use the slice function
    
    function confirmEnding(str, target) {
      // "Never give up and good luck will find you."
      // -- Falcor
      var str2, str3 = '';
      for (var i = 0; i < str.length; i++) {
        str2 = str.slice(-target.length, str.length);
        if (str2 === target) {
          return true;
        } else {
          return false;
        }
      }
    }
    console.log('result ', confirmEnding("Congratulation", "on"));
```
## <a name="repeatS"/> Repeat a String Repeat a String
Truncate a string (first argument) 
if it is longer than the given maximum string length (second argument). 
Return the truncated string with a ... ending.


```
// And we did it again !!!
// This time without even a hint.
// I did google for converting an array to a 
// string and I got the join() function

    function repeatStringNumTimes(str, num) {
      // repeat after me
      var arr = [];
      
      if (num < 0) {
        return '';
      } else {
        for (var i = 0; i < num; i++) {
          arr.push(str);
        }
        return arr.join('');
      }
    }
    console.log(repeatStringNumTimes("*", 8));

```
## <a name="truncateS"/> Truncate a String
```
  // We need to reduce the length of the string or truncate it 
    // if it is longer than the given maximum lengths specified 
    // and add ... to the end. If it is not that long then we keep it 
    // as is.

    // And yes we did it again! :)
    // Truncate a string (first argument) if it is longer
    // than the given maximum string length (second argument).
    // Return the truncated string with a ... ending
    function truncateString(str, num) {
      // Clear out that junk in your trunk
      let temp = '';

      temp = str.slice(0, num);
      temp += "..."
      console.log(temp);
      if (str.length <= num) {
        return str;
      } else {
        return temp.slice(0, num + 3);
      }
    }
    console.log('result ', truncateString("A-tisket a-tasket A green and yellow basket", "A-tisket a-tasket A green and yellow basket".length + 2));

```
 
   ## <a name="findK"/>Finders Keepers
    Create a function that looks through an array (first argument)
    and returns the first element in the array that passes a truth test
    (second argument).
    If no element passes the test, return undefined.

    Yes we did it again, without even a hint.
    Note in the code below this:( func(arr[i]) === true)
    is not needed. I could just do this:
    (func(arr[i])).
    Moreover I could just assign the arr[i] to num and return it.
    If there was no match 'undefined' would return by default.
    Well not literly. It just returns nothing.
   
   ```
   
   // FCC solution
    function findElement(arr, func) {
      let num = 0;
      for (let i = 0; i < arr.length; i++) {
        console.log(func(arr[i]));
        if (func(arr[i]) === true) {
          return num = arr[i] ? arr[i] : 'undefined';
          console.log(num);
        }
      }
    }

    console.log(findElement([1, 3, 8, 9], function(num) {
      return num % 2 === 0;
    }));
```

  ## <a name="checkBoolean"/> Boo who. Check if a value is classified as a boolean primitive.
       
 ```
     Return true or false.
     This one doesn't work with arrays
    function booWho(bool) {
      // What is the new fad diet for ghost developers? The Boolean.

      return Number.isInteger(bool) ? false : bool ? true : false
    }
    console.log(booWho(false));

    
    This is one does the job. YES !!!
        function booWho(bool) {
          // What is the new fad diet for ghost developers? The Boolean.
          if (bool === true || bool === false) {
            return true;
          } else {
            return false;
          }
        }

        console.log(booWho({
          "a": 1
       }));
 ```
```
    FCC Solution
    function booWho(bool) {
          return typeof bool === 'boolean';
        }

        // test here
        booWho(null);
```

## <a name="titleCase"/> Title Case a Sentence [FCC Solutions](https://guide.freecodecamp.org/certifications/javascript-algorithms-and-data-structures/basic-algorithm-scripting/title-case-a-sentence)
Return the provided string with the first letter of each word capitalized. Make sure the rest of the word is in lower case.

I got a lot of help from Randell Dawson.
Here is the topic on the [forum.](https://www.freecodecamp.org/forum/t/title-case-a-sentence-is-there-any-chance-for-this-code-to-work/231456/7)

```
  // This one is with the replace method.
        function titleCase(str) {

          // make all leters toLowerCase and convert str to array
          let arr = str.toLowerCase().split(' ');
          let arr1 = []

          for (var i = 0; i < arr.length; i++) {


            console.log('each word ', arr[i]);
            console.log('first letter ', arr[i].charAt(0));
            console.log('first letter capitalized ', arr[i].charAt(0).toUpperCase());

            // On each word replace the first letter with a capitalized one.
            arr1.push(arr[i].replace(arr[i].charAt(0), arr[i].charAt(0).toUpperCase()));


            console.log(arr1);

          }

          return arr1.join(' ');
        }
        console.log('result: ', titleCase("I'm a little tea pot"));

```
Second way. 

```
  // this one is with slice
    function titleCase(str) {

      // make all leters toLowerCase and convert str to array
      let arr = str.toLowerCase().split(' ');

      let arr2 = []
      for (let i = 0; i < arr.length; i++) {

        var firstLetter = arr[i][0].toUpperCase();
        //console.log(firstLetter);

        // slice the rest of the arr[i] word
        var restOfWord = arr[i].slice(1);
        //console.log(restOfWord);

        arr2.push(firstLetter += restOfWord);
        //console.log('FL ', firstLetter);

      }

      // concat the two arrays
      return arr2.join(' ');

    }

    console.log('result: ', titleCase("sHoRt AnD sToUtt"));
    // result:  Short And Stoutt

```
  ## <a name="sliceSplice"/> Slice and Splice
    You are given two arrays and an index.
    Use the array methods slice and splice to copy each
    element of the first array into the second array, in order.
    Begin inserting elements at index n of the second array.
    Return the resulting array.
    The input arrays should remain the same after the function runs.

    First solution (without a hint).
    But, I found the way to flatten the result array
    from the internet. 

```
    function frankenSplice(arr1, arr2, n) {
      // It's alive. It's alive!
      let arr3 = [...arr2];
      let arr4 = [];
    
      arr3.splice(n, 0, arr1.slice(0))
      arr4 = [].concat.apply([], arr3)
      console.log(arr3);
    
      return arr4;
    }
    
    console.log(frankenSplice([1, 2], ["a", "b"], 1));
```
FCC Solution.
That's what I was trying to do in the first place,
but I was iterating in the second array
    
    
```
function frankenSplice(arr1, arr2, n) {
      // It's alive. It's alive!
      let arr3 = [...arr2];
      let arr4 = [];
      
      for (var i = 0; i < arr1.length; i++) {
        arr3.splice(n, 0, arr1[i])
    
      }
      console.log(arr3);
    
      return arr3;
    }
    
    console.log(frankenSplice([1, 2], ["a", "b"], 1));
 ```
  Another nice way found in the forum
    That's what I was trying to do in the first place,
    but instead of ...arr1, I was using
    1.  [...arr1]
    2. newArr.splice(n, 0, arr1.slice(0));
    So I was getting the array as a whole.
```
  function frankenSplice(arr1, arr2, n) {
      // It's alive. It's alive!
      var newArr = arr2.slice(0);
      newArr.splice(n, 0, ...arr1); // also works ...arr1
      return newArr;
    }
    console.log(frankenSplice([1, 2], ["a", "b"], 1));
```

  # Falsy Bouncer <a name="falsyBouncer"/> 
    Remove all falsy values from an array.
    Falsy values in JavaScript are false, null, 0, "", undefined, and NaN.
    Hint: Try converting each value to a Boolean.
```
    // Got it in a few minutes! ;)
    function bouncer(arr) {
      // Don't show a false ID to this bouncer.
      let arr1 = [];

      for (var i = 0; i < arr.length; i++) {
        if (arr[i]) {
          arr1.push(arr[i])
        }
      }
      return arr1;
    }
  console.log('result', bouncer([7, "ate", "", false, 9]));
    // result (3) [7, "ate", 9]
```

  FCC Advanced Solution
```
    function bouncer(arr) {
      return arr.filter(Boolean);
    }
    console.log('result', bouncer([7, "ate", "", false, 9]));
```

 ## <a name="whereBelong"/> Where do I Belong [FCC Solutions](https://guide.freecodecamp.org/certifications/javascript-algorithms-and-data-structures/basic-algorithm-scripting/where-do-i-belong/)
Return the lowest index at which a value (second argument) should be inserted into an array (first argument) once it has been sorted. The returned value should be a number.
For ex. getIndexToIns([20,3,5], 19) should return 2 because once the array has been sorted it will look like [3,5,20] and 19 is less than 20 (index 2) and greater than 5 (index 1).
There are more siple solutions in FCC/
I always try to hard to be smart, I quess.
Or is it because I'm new to programming.
   
```
    function getIndexToIns(arr, num) {
      // Find my place in this sorted array.
      // Found a way in stackOverflow to sort an array in a for loop
      let output = [];
      for (var i = 0; i < arr.length; i++) {
        for (var j = 0; j < i; j++) { // first time see this
          if (arr[i] < arr[j]) {
            var temp = arr[i]; // very nice trick the rest
            arr[i] = arr[j];
            arr[j] = temp
          }
        }
        //  console.log(arr);
      }
      // get the index of num
      for (var i = 0; i < arr.length; i++) {
        if (arr[i] < num) {
          output.push(arr[i]);
        } else {
          output.push(num)
        }
      }
      if (output.indexOf(num) === -1) {
        output.push(num)
      }
      console.log(output);
      console.log(output.indexOf(num));
      return output.indexOf(num);
    }

    console.log(getIndexToIns([2, 5, 10], 15));
    output: 3
    ```
    
    ```
      // using the sort method
    function getIndexToIns(arr, num) {

      let output = [];
      // Find my place in this sorted array.
      arr.sort(function CompareForSort(first, second) {
        if (first == second)
          return 0;
        if (first < second)
          return -1;
        else
          return 1;
      });


      // get the index of num
      for (var i = 0; i < arr.length; i++) {
        if (arr[i] < num) {
          output.push(arr[i]);
        } else {
          output.push(num)
        }
      }
       // check if the array is finished
      if (output.indexOf(num) === -1) {
        output.push(num)
      }
      console.log(output);
      console.log(output.indexOf(num));
      return output.indexOf(num);
    }

    console.log(getIndexToIns([2, 5, 10], 15));
    // output 3
```
 ## <a name="mutations"/>Mutations   

```
    // Return true if the string in the first element of
    // the array contains all of the letters of the string
    // in the second element of the array.
    // For example, ["hello", "Hello"], should return true
    // because all of the letters in the second string are present
    // in the first, ignoring case.

    // I DID AGAIN !!!
    function mutation(arr) {

      let arr1 = [...arr[0]];
      let arr2 = [...arr[1]];
      let counter = 0
      for (var i = 0; i < arr2.length; i++) {
        //console.log('arr2 = ', arr2[i]);

        for (var j = 0; j < arr1.length; j++) {
          //  console.log('arr1 = ', arr1[j]);
          if (arr2[i].toUpperCase() === arr1[j].toUpperCase()) {
            counter++
            break;
          }
        }
      }
      console.log(counter);
      console.log(arr2.length);
      if (counter === arr2.length) {
        return true;
      } else {
        return false;
      }
    }
    console.log(mutation(["hello", "Heblo"]));
// output: false
```
```
    // FCC Solution
    function mutation(arr) {
      var test = arr[1].toLowerCase();
      var target = arr[0].toLowerCase();

      // Iterate over the second word 
      // and check if each letter of it => test[i]
      // is also an indexOf target, which is 
      // the first word.If indexOf is not found 
      // it returns -1. So...
      for (var i = 0; i < test.length; i++) {
        if (target.indexOf(test[i]) < 0)
          return false;
      }
      return true;
    }

    console.log(mutation(["hello", "Heblo"]));
```
[Go up](#goUp)

## <a name= "chunkyMonkey"/>Chunky Monkey. 
[Click here to check the FCC Solutions](https://guide.freecodecamp.org/certifications/javascript-algorithms-and-data-structures/basic-algorithm-scripting/chunky-monkey/)

```
    // Write a function that splits an array (first argument)
    // into groups the length of size (second argument)
    // and returns them as a two-dimensional array.
    // Yes!!! We did it!
    function chunkArrayInGroups(arr, size) {
      // Break it up.
      let newArr = [];
      let chop = 0;
      let monkey = size

      // iterate throu the array
      for (var i = 0; i < arr.length; i++) {

        // make sure that second value of slice is less
        // than the array's length
        if (monkey < arr.length) {

          // chop the first piece
          newArr.push(arr.slice(chop, monkey));
          console.log(chop, ' ', monkey);

          // increment the values of slice to chop the next piece.
          chop += size;
          monkey = chop + size;
          console.log(arr.length);

          // if the second value of slice if bigger than the
          // arr.length, then use the arr.length
        } else {
          newArr.push(arr.slice(chop, arr.length));

          // The monkey value will exeed the arrays length
          // So we need to break, so it will not output
          // the last piece more times...
          break;
        }
      }
      return newArr;
    }

    console.log(chunkArrayInGroups([0, 1, 2, 2, 2, 2, 3, 4, 5], 3));
```
FCC Solution
```
   // Nice and simple
  function chunkArrayInGroups(arr, size) {
      // Break it up.
      var arr2 = [];
      for (var i = 0; i < arr.length; i+=size) {
    	arr2.push(arr.slice(i , i+size));
      }
      return arr2;
    }
    
```
This FCC Solution is even better
```
 function chunkArrayInGroups(arr, size) {
      // Break it up.
      var newArr = [];
      var i = 0;

      while (i < arr.length) {
        newArr.push(arr.slice(i, i+size));
        i += size;
      }
      return newArr;
    }
    chunkArrayInGroups(["a", "b", "c", "d"], 2);
```
This piece of code is amazing!
It just chops off the array until there's nothing left,
and arr.length is 0.
I feel stupid.
```
  function chunkArrayInGroups(arr, size) {
      var newArr = [];
      while (arr.length) {
        newArr.push(arr.splice(0, size));
      }
      return newArr;
    }

    console.log(chunkArrayInGroups([0, 1, 2, 3, 4, 5], 4));
```

An interesting one from the forum. [Click here to check the post](https://www.freecodecamp.org/forum/t/help-needed-in-chunky-monkey-problem/31907/4).
I did put some comments for undestanding.

```
     function chunkArrayInGroups(arr, size) {
      var ans = [];
      var count = 0;
      // how many times chop the array
      times = Math.ceil(arr.length / size);
      //  console.log('times', times);

      // So we need to iterate only two times in this case
      for (var i = 0; i < times; i++) {

        // temp is going to hold temporarily each choped array.
        var temp = [];
        //  console.log('temp =', temp);

        // get each element, according to size
        // and store it in temp
        for (var j = 0; j < size; j++) {
          if (count < arr.length) {
            temp.push(arr[count]);
            //  console.log('arr[count] =', arr[count]);
          }
          // move to next element
          count++;
          //  console.log('count', count);
          //  console.log(temp);
        }
        // push all those broken pieces into another array
        ans.push(temp);
      }
      return ans;
    }

    console.log(chunkArrayInGroups([0, 1, 68, 87, 8, 5], 4));
```
Code with most likes in forum of FCC [Click here to check the post](https://www.freecodecamp.org/forum/t/chunky-monkey-under-basic-algorithm-scripting-question/3838/6)

```
    function chunkArrayInGroups(arr, size) {

      var arraySize = arr.length / size;
      console.log('arraySize', arraySize);

      var newArray = [];

      for (var i = 0; i < arraySize; i++) {

        var subArray = arr.splice(0, size);

        newArray.push(subArray);

      }

      return newArray;

    }

    console.log(chunkArrayInGroups([0, 1, 68, 87, 8, 5], 4));
```
[Go up](#goUp)



    
