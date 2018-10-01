# freeCodeCamp
Here are my solutions to the challenges. They are not the best, but they show my progression. 

## Basic Algorithm Scripting

```
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
