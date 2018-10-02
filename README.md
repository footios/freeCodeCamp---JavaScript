# freeCodeCamp 
Here are my solutions to the challenges. They are not the best, but they show my progression. 

## Basic Algorithm Scripting

* Basic Algorithm Scripting: Return Largest Numbers in Arrays
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

Basic Algorithm Scripting: Return Largest Numbers in Arrays
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
// FCC solution
    //  Advanced Code Solution:
    //  (Declarative approach)
```




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
# Confirm the Ending
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
# Truncate a String
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
