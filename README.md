# freeCodeCamp  Challenges
Here are my solutions to the challenges. They are not the best, but they show my progression. 

* [Basic Algorithm Scripting](#basicAlgo)
    * [Return Largest Numbers in Arrays](#returnL)
    * [Confirm Ending](#confirmE)
    * [Repeat a String Repeat a String](#repeatS)
    * [Truncate a String](#truncateS) 
    * [Finders Keepers](#findK)
    * [Check for boolean](#checkBoolean)
    * [Title Case a Sentence](#titleCase)
    * [Slice and Splice](#sliceSplice)
    






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
