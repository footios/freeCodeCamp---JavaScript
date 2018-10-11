# freeCodeCamp  Challenges <a name="goUp"/>
> (2018 / September - October)
>
> Here are my solutions to the challenges. 
> 
> They are not the best solutions, but they show my progress.
> 
> Note. Here come only the challenges I've found hard to pass. 
> 
> Spool up the FTL drive!

* [9. Intermediate Algorithm Scripting](#InterAlgo)
    * [Sum All Numbers in a Range](#sumNum)
    * [Factoralize number](#factoralize)
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
       
     
    
# <a name="InterAlgo"/> Intermediate Algorithm Scripting


## <a name="sumNum"/> Sum All Numbers in a Range]

```
    function sumAll(arr) {
      let temp = [];
      temp = arr.sort((a, b) => a - b);

      let total = 0;
      total = temp.reduce((a, b) => {
        let numbers = [];
        console.log(numbers);
        do {
          numbers.push(b--);
        } while (a <= b);

        let sum = 0;
        sum = numbers.reduce((a, b) => a + b);
        return sum;
      })
      return total;
    }

    console.log(sumAll([10, 5]));
    
```

[Go up](#goUp)
