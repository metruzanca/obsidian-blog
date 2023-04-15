
## [BentoBox](https://www.getbento.com/) Interview


### Coding
```ts
// Write a function that returns integers between identical integers
// input = [2, 3, 4, 2, 3, 5]
// output = [3, 4, 4, 2]

function identicalIntegers(array: number[]) {
  const map = new Map()
  const result: number[] = []
  for (let i = 0; i < array.length; i++) {
    const currentValue = array[i]
    const lastPosition = map.get(currentValue)
    const previousValue = array[lastPosition]

    if (previousValue === currentValue) {
      result.push(...array.slice(lastPosition + 1, i)) //todo
    }

    map.set(currentValue, i)
  }
  return result
}


console.log(identicalIntegers([2, 3, 4, 2, 3, 5])); //3, 4, 4, 2

console.log(identicalIntegers([2,2])); // 
console.log(identicalIntegers([])); //
console.log(identicalIntegers([1,2,3,4,5])); //

console.log(identicalIntegers([2,1,2,3,2])); // 1,3
console.log(identicalIntegers([2,1,2,1,2])); // 1,2,1
```

### Questions
**A day in the life?**



**Culture**



**Benefits? 401k?**



**Growth opportunities? Feedback? Monthly/quarterly Reviews? Mentors?**



**What's your flavor of Agile?** **Team Size?**



**How long are (client) projects?**




**What would I be working on?**



**What type of skills is the team missing that you're looking to fill with a new hire?**
