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
  //Now it's working, but i show the solution
    // and the main mistake (if not the lonly one)
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

       My question is why the second for loop iterates
       over the first sub array and then jumbs back to first
       for loop and starts iterating over the second
       sub array?

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
