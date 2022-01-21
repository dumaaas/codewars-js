<template>
  <div class="main">
    <div class="container">
      <div class="cards">
        <div class="card" :class="{ 'card-active': task1 }">
          <h1 class="title">Task 1</h1>
          <p class="description">
            Write a function that takes in a string of one or more words, and
            returns the same string, but with all five or more letter words
            reversed(Just like the name of this Kata). Strings passed in will
            consist of only letters and spaces. Spaces will be included only
            when more than one word is present.
          </p>
          <div class="card-flex">
            <input
              v-model="wordSpin"
              @focus="task1 = true"
              @blur="task1 = false"
            />
            <p v-if="wordSpin">{{ spinWords(wordSpin) }}</p>
          </div>
        </div>
        <div class="card" :class="{ 'card-active': task2 }">
          <h1 class="title">Task 2</h1>
          <p class="description">
            Trolls are attacking your comment section! A common way to deal with
            this situation is to remove all of the vowels from the trolls'
            comments, neutralizing the threat. Your task is to write a function
            that takes a string and return a new string with all vowels removed.
            For example, the string "This website is for losers LOL!" would
            become "Ths wbst s fr lsrs LL!". Note: for this kata y isn't
            considered a vowel.
          </p>
          <div class="card-flex">
            <input
              v-model="wordDisemvowel"
              @focus="task2 = true"
              @blur="task2 = false"
            />
            <p v-if="wordDisemvowel">{{ disemvowel(wordDisemvowel) }}</p>
          </div>
        </div>
        <div class="card" :class="{ 'card-active': task3 }">
          <h1 class="title">Task 3</h1>
          <p class="description">
            Count the number of Duplicates Write a function that will return the
            count of distinct case-insensitive alphabetic characters and numeric
            digits that occur more than once in the input string. The input
            string can be assumed to contain only alphabets (both uppercase and
            lowercase) and numeric digits.
          </p>
          <div class="card-flex">
            <input
              v-model="wordDuplicateCount"
              @focus="task3 = true"
              @blur="task3 = false"
            />
            <p v-if="wordDuplicateCount">
              {{ duplicateCount(wordDuplicateCount) }}
            </p>
          </div>
        </div>
        <div class="card" :class="{ 'card-active': task4 }">
          <h1 class="title">Task 4</h1>
          <p class="description">
            Given an integral number, determine if it's a square number: In
            mathematics, a square number or perfect square is an integer that is
            the square of an integer; in other words, it is the product of some
            integer with itself. The tests will always use some integral number,
            so don't worry about that in dynamic typed languages.
          </p>
          <div class="card-flex">
            <input
              v-model="wordIsSquare"
              @focus="task4 = true"
              @blur="task4 = false"
            />
            <p v-if="wordIsSquare">
              {{ isSquare(wordIsSquare) }}
            </p>
          </div>
        </div>
        <div class="card" :class="{ 'card-active': task5 }">
          <h1 class="title">Task 5</h1>
          <p class="description">
            Implement a function that accepts 3 integer values a, b, c. The
            function should return true if a triangle can be built with the
            sides of given length and false in any other case. (In this case,
            all triangles must have surface greater than 0 to be accepted).
          </p>
          <div class="card-flex card-flex__col">
            <input
              v-model="wordIsTriangleA"
              @focus="task5 = true"
              @blur="task5 = false"
            />
            <input
              v-model="wordIsTriangleB"
              @focus="task5 = true"
              @blur="task5 = false"
            />
            <input
              v-model="wordIsTriangleC"
              @focus="task5 = true"
              @blur="task5 = false"
            />

            <p v-if="wordIsTriangleA && wordIsTriangleB && wordIsTriangleC">
              {{
                isTriangle(wordIsTriangleA, wordIsTriangleB, wordIsTriangleC)
              }}
            </p>
          </div>
        </div>
        <div class="card" :class="{ 'card-active': task6 }">
          <h1 class="title">Task 6</h1>
          <p class="description">
            Move the first letter of each word to the end of it, then add "ay"
            to the end of the word. Leave punctuation marks untouched.
          </p>
          <div class="card-flex">
            <input
              v-model="wordPigIt"
              @focus="task6 = true"
              @blur="task6 = false"
            />
            <p v-if="wordPigIt">
              {{ pigIt(wordPigIt) }}
            </p>
          </div>
        </div>
        <div class="card" :class="{ 'card-active': task7 }">
          <h1 class="title">Task 7</h1>
          <p class="description">
            Digital root is the recursive sum of all the digits in a number.
            Given n, take the sum of the digits of n. If that value has more
            than one digit, continue reducing in this way until a single-digit
            number is produced. The input will be a non-negative integer.
          </p>
          <div class="card-flex">
            <input
              v-model="wordDigitalRoot"
              @focus="task7 = true"
              @blur="task7 = false"
            />
            <p v-if="wordDigitalRoot">
              {{ digitalRoot(wordDigitalRoot) }}
            </p>
          </div>
        </div>
        <div class="card" :class="{ 'card-active': task8 }">
          <h1 class="title">Task 8</h1>
          <p class="description">
            Implement the function unique_in_order which takes as argument a
            sequence and returns a list of items without any elements with the
            same value next to each other and preserving the original order of
            elements.
          </p>
          <div class="card-flex">
            <input
              v-model="wordUniqueInOrder"
              @focus="task8 = true"
              @blur="task8 = false"
            />
            <p v-if="wordUniqueInOrder">
              {{ uniqueInOrder(wordUniqueInOrder) }}
            </p>
          </div>
        </div>
        <div class="card" :class="{ 'card-active': task9 }">
          <h1 class="title">Task 9</h1>
          <p class="description">
            Given a list lst and a number N, create a new list that contains
            each number of lst at most N times without reordering. For example
            if N = 2, and the input is [1,2,3,1,2,1,2,3], you take [1,2,3,1,2],
            drop the next [1,2] since this would lead to 1 and 2 being in the
            result 3 times, and then take 3, which leads to [1,2,3,1,2,3].
          </p>
          <div class="card-flex card-flex__col">
            <p>{{ arrayDeleteNth }}</p>
            <input
              v-model="wordDeleteNth"
              @focus="task9 = true"
              @blur="task9 = false"
            />
            <p v-if="wordDeleteNth">
              {{ deleteNth(wordDeleteNth) }}
            </p>
          </div>
        </div>
        <div class="card" :class="{ 'card-active': task10 }">
          <h1 class="title">Task 10</h1>
          <p class="description">
            Some numbers have funny properties. For example: 695 --> 6² + 9³ +
            5⁴= 1390 = 695 * 2 Given a positive integer n written as abcd... (a,
            b, c, d... being digits) and a positive integer p we want to find a
            positive integer k, if it exists, such as the sum of the digits of n
            taken to the successive powers of p is equal to k * n. If it is the
            case we will return k, if not return -1. Note: n and p will always
            be given as strictly positive integers.
          </p>
          <div class="card-flex card-flex__col">
            <input
              v-model="wordDigPowA"
              @focus="task10 = true"
              @blur="task10 = false"
            />
            <input
              v-model="wordDigPowB"
              @focus="task10 = true"
              @blur="task10 = false"
            />

            <p v-if="wordDigPowA && wordDigPowB">
              {{ digPow(wordDigPowA, wordDigPowB) }}
            </p>
          </div>
        </div>
        <div class="card" :class="{ 'card-active': task11 }">
          <h1 class="title">Task 11</h1>
          <p class="description">
            Write a function, persistence, that takes in a positive parameter
            num and returns its multiplicative persistence, which is the number
            of times you must multiply the digits in num until you reach a
            single digit.
          </p>
          <div class="card-flex">
            <input
              v-model="wordPersistance"
              @focus="task11 = true"
              @blur="task11 = false"
            />

            <p v-if="wordPersistance">
              {{ persistence(wordPersistance) }}
            </p>
          </div>
        </div>
        <div class="card" :class="{ 'card-active': task12 }">
          <h1 class="title">Task 12</h1>
          <p class="description">
            You are given an array(list) strarr of strings and an integer k.
            Your task is to return the first longest string consisting of k
            consecutive strings taken in the array.n being the length of the
            string array, if n = 0 or k > n or k less or equal to 0 return "".
            Note -> consecutive strings : follow one after another without an
            interruption
          </p>
          <div class="card-flex card-flex__col">
            <p>{{ arrayLongestConsec }}</p>
            <input
              v-model="wordLongestConsec"
              @focus="task12 = true"
              @blur="task12 = false"
            />
            <p v-if="wordLongestConsec">
              {{ longestConsec(wordLongestConsec) }}
            </p>
          </div>
        </div>
        <div class="card" :class="{ 'card-active': task13 }">
          <h1 class="title">Task 13</h1>
          <p class="description">
            There is a queue for the self-checkout tills at the supermarket.
            Your task is write a function to calculate the total time required
            for all the customers to check out! Clarifications -> There is only
            ONE queue serving many tills, and The order of the queue NEVER
            changes, and The front person in the queue (i.e. the first element
            in the array/list) proceeds to a till as soon as it becomes free.
          </p>
          <div class="card-flex card-flex__col">
            <p>{{ arrayQueueTime }}</p>
            <input
              v-model="wordQueueTime"
              @focus="task13 = true"
              @blur="task13 = false"
            />
            <p v-if="wordQueueTime">
              {{ queueTime(wordQueueTime) }}
            </p>
          </div>
        </div>
        <div class="card" :class="{ 'card-active': task14 }">
          <h1 class="title">Task 14</h1>
          <p class="description">
            Write a program that will calculate the number of trailing zeros in
            a factorial of a given number. N! = 1 * 2 * 3 * ... * N. Be careful
            1000! has 2568 digits...
          </p>
          <div class="card-flex">
            <input
              v-model="wordZeros"
              @focus="task14 = true"
              @blur="task14 = false"
            />
            <p v-if="wordZeros">
              {{ zeros(wordZeros) }}
            </p>
          </div>
        </div>
        <div class="card" :class="{ 'card-active': task15 }">
          <h1 class="title">Task 15</h1>
          <p class="description">
            You are given an array(list) strarr of strings and an integer k.
            Your task is to return the first longest string consisting of k
            consecutive strings taken in the array.n being the length of the
            string array, if n = 0 or k > n or k less or equal to 0 return "".
            Note -> consecutive strings : follow one after another without an
            interruption
          </p>
          <div class="card-flex card-flex__col">
            <p>{{ arraySumOfDivided }}</p>

            <p>
              {{ sumOfDivided() }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  data() {
    return {
      task1: false,
      task2: false,
      task3: false,
      task4: false,
      task5: false,
      task6: false,
      task7: false,
      task8: false,
      task9: false,
      task10: false,
      task11: false,
      task12: false,
      task13: false,
      task14: false,
      task15: false,
      wordSpin: '',
      wordDisemvowel: '',
      wordDuplicateCount: '',
      wordIsSquare: '',
      wordIsTriangleA: '',
      wordIsTriangleB: '',
      wordIsTriangleC: '',
      wordPigIt: '',
      wordDigitalRoot: '',
      wordUniqueInOrder: '',
      wordDeleteNth: '',
      arrayDeleteNth: [20, 37, 20, 21, 21, 21, 2, 2, 1, 5, 4, 21],
      wordDigPowA: '',
      wordDigPowB: '',
      wordPersistance: '',
      wordLongestConsec: '',
      arrayLongestConsec: ['it', 'wkppv', 'ixoyx', '3452', 'zzzzzzzzzzzz'],
      wordQueueTime: '',
      wordZeros: '',
      arrayQueueTime: [23, 15, 21, 27, 35, 14, 13],
      wordSumOfDivided: '',
      arraySumOfDivided: [4, 7, -21, 38, 29, 11, -49],
    }
  },
  methods: {
    // Task 1

    // Write a function that takes in a string of one or more words, and returns the same string,
    // but with all five or more letter words reversed(Just like the name of this Kata).
    // Strings passed in will consist of only letters and spaces.
    // Spaces will be included only when more than one word is present.

    spinWords(string) {
      const strings = string.split(' ')
      strings.forEach((string, index) => {
        if (string.length > 4) {
          string = string.split('').reverse().join('')
          strings[index] = string
        }
      })
      console.log(strings.join(' '))
      return strings.join(' ')
    },

    // Task 2

    // Trolls are attacking your comment section!
    // A common way to deal with this situation is to remove all of the vowels from the trolls' comments, neutralizing the threat.
    // Your task is to write a function that takes a string and return a new string with all vowels removed.
    // For example, the string "This website is for losers LOL!" would become "Ths wbst s fr lsrs LL!".
    // Note: for this kata y isn't considered a vowel.

    disemvowel(str) {
      // g tells to find all matches, not just the first.
      // i tells to be case insensitive
      // What goes inside the // is the pattern
      // [] tells to match any character in set
      // aeiou are the characters in the set.
      console.log(str.replace(/[aeiou]/gi, ''))
      return str.replace(/[aeiou]/gi, '')
    },

    // Task 3

    // Count the number of Duplicates
    // Write a function that will return the count of distinct case-insensitive alphabetic characters and numeric digits that occur more
    // than once in the input string. The input string can be assumed to contain only alphabets (both uppercase and lowercase) and numeric digits.

    duplicateCount(str) {
      // case-insensitive + transform to array
      str = str.toLowerCase().split('')
      // array of duplicate elements in str
      let findDuplicates = (arr) =>
        arr.filter((item, index) => arr.indexOf(item) != index)
      // Set is storing only unique value of each value in array, so we are using size to tell us how many duplicates were in array
      let countUnique = (arr) => {
        return new Set(arr).size
      }
      console.log(countUnique(findDuplicates(str)))
      return countUnique(findDuplicates(str))
    },

    // Task 4

    // Given an integral number, determine if it's a square number:
    // In mathematics, a square number or perfect square is an integer that is the square of an integer; in other words, it is the product of some integer with itself.
    // The tests will always use some integral number, so don't worry about that in dynamic typed languages.

    isSquare(n) {
      // if sqrt is rounded number
      return Math.sqrt(n) % 1 === 0
    },

    // Task 5

    // Implement a function that accepts 3 integer values a, b, c. The function should return true
    // if a triangle can be built with the sides of given length and false in any other case.
    // (In this case, all triangles must have surface greater than 0 to be accepted).

    isTriangle(a, b, c) {
      // The sum of the lengths of any two sides of a triangle
      // must be greater than the length of the third side.
      a = parseInt(a)
      b = parseInt(b)
      c = parseInt(c)

      return a + b > c && a + c > b && c + b > a
    },

    // Task 6

    // Move the first letter of each word to the end of it, then add "ay" to the end of the word. Leave punctuation marks untouched.

    pigIt(str) {
      str = str.split(' ')
      str.forEach((s, index) => {
        if (s.match(/[a-z]/gi)) {
          s = s.substr(1) + s.substr(0, 1) + 'ay'
          str[index] = s
        }
      })
      console.log(str.join(' '))
      return str.join(' ')
    },

    // Task 7

    // Digital root is the recursive sum of all the digits in a number.
    // Given n, take the sum of the digits of n. If that value has more than one digit,
    // continue reducing in this way until a single-digit number is produced. The input will be a non-negative integer.

    digitalRoot(n) {
      var root = 0

      // convert number to string, then to array of strings
      // for each of array elements parse string back to int and add it to root
      n.toString()
        .split('')
        .forEach((item) => {
          root += parseInt(item)
        })

      // if root is smaller then 10 return that value
      // if is not, call our function again
      return root < 10 ? root : this.digitalRoot(root)
    },

    // Task 8

    // Implement the function unique_in_order which takes as argument a sequence and returns a list of items
    // without any elements with the same value next to each other and preserving the original order of elements.

    uniqueInOrder(iterable) {
      // if string, split into array
      if (typeof iterable == 'string') {
        iterable = iterable.split('')
      }
      // while element next to the current is same, remove it from array
      iterable.forEach((item, index) => {
        while (item === iterable[index + 1]) {
          iterable.splice(index + 1, 1)
        }
      })
      // return array without any element with same value next to each other
      return iterable.join('')
    },

    // Task 9

    // Given a list lst and a number N, create a new list that contains each number of lst at most N times without reordering.
    // For example if N = 2, and the input is [1,2,3,1,2,1,2,3], you take [1,2,3,1,2], drop the next [1,2] since this would lead
    // to 1 and 2 being in the result 3 times, and then take 3, which leads to [1,2,3,1,2,3].

    deleteNth(n) {
      let totals = {}
      var arr = [...this.arrayDeleteNth]
      return arr.filter((o) => (totals[o] = ++totals[o] || 0) < n)
    },

    // Task 10

    // Some numbers have funny properties. For example:
    // 695 --> 6² + 9³ + 5⁴= 1390 = 695 * 2
    // Given a positive integer n written as abcd... (a, b, c, d... being digits) and a positive integer p
    // we want to find a positive integer k, if it exists, such as the sum of the digits of n taken to the successive powers of p is equal to k * n.
    // If it is the case we will return k, if not return -1.
    // Note: n and p will always be given as strictly positive integers.

    digPow(n, p) {
      n = n.split('')
      var sum = 0
      var pow = p
      // counting sum of every digit of number on incrementing pows
      n.forEach((item) => {
        sum = sum + Math.pow(item, pow)
        pow++
      })
      n = n.join('')
      // if sum equal original number is equal is integer
      // we return that number
      // else return -1
      return sum % n === 0 ? sum / n : -1
    },

    // Task 11

    // Write a function, persistence, that takes in a positive parameter num and returns its multiplicative persistence,
    // which is the number of times you must multiply the digits in num until you reach a single digit.
    // For example (Input --> Output):
    // 39 --> 3 (because 3*9 = 27, 2*7 = 14, 1*4 = 4 and 4 has only one digit)

    persistence(num) {
      // number of multiplicative persistence
      var times = 0

      // repeat this while num have 2+ digits
      while (num.length > 1) {
        // increment number of multiplicative persistence
        times++
        // split number into an array
        // go through every element of array and multiple previousValue with newValue
        num = num
          .split('')
          .reduce((a, b) => a * b)
          .toString()
      }
      // return number of multiplicative persistence
      return times
    },

    // Task 12

    // You are given an array(list) strarr of strings and an integer k. Your task is to return
    // the first ongest string consisting of k consecutive strings taken in the array.
    // n being the length of the string array, if n = 0 or k > n or k <= 0 return "" (return Nothing in Elm).
    // Note
    // consecutive strings : follow one after another without an interruption

    longestConsec(k) {
      k = parseInt(k)

      if (
        this.arrayLongestConsec.length === 0 ||
        k > this.arrayLongestConsec.length ||
        k <= 0
      )
        return 'Try another number.'
      var result = ''
      for (let i = 0; i <= this.arrayLongestConsec.length - k; i++) {
        var str = ''
        for (let j = i; j < i + k; j++) {
          str += this.arrayLongestConsec[j]
        }
        if (result.length < str.length) {
          result = str
        }
      }
      return result
    },

    // Task 13

    // here is a queue for the self-checkout tills at the supermarket. Your task is write a function
    // to calculate the total time required for all the customers to check out!
    // Clarifications ->
    // There is only ONE queue serving many tills, and
    // The order of the queue NEVER changes, and
    // The front person in the queue (i.e. the first element in the array/list) proceeds to a till as soon as it becomes free.

    queueTime(n) {
      n = parseInt(n)
      let arr = []

      for (let i = 0; i < n; i++) arr[i] = 0

      for (let i = 0; i < this.arrayQueueTime.length; i++) {
        arr[0] += this.arrayQueueTime[i]
        arr.sort((a, b) => a - b)
      }

      return arr[arr.length - 1]
    },

    // Task 14

    // Write a program that will calculate the number of trailing zeros in a factorial of a given number.
    // N! = 1 * 2 * 3 * ... * N
    // Be careful 1000! has 2568 digits...

    zeros(n) {
      n = parseInt(n)
      if (n < 0)
        //Negative Number Edge Case
        return 'Try number >= 0'

      // Initialize result
      let count = 0

      // keep dividing n by powers of 5 and update count
      while (n > 0) {
        n = Math.floor(n / 5)
        count += n
      }
      return count
    },

    // Task 15

    // Given an array of positive or negative integers
    // I= [i1,..,in]
    // you have to produce a sorted array P of the form
    // [ [p, sum of all ij of I for which p is a prime factor (p positive) of ij] ...]
    // P will be sorted by increasing order of the prime numbers. The final result has to be given as a string in Java, C#, C, C++ and as an array of arrays in other languages.

    sumOfDivided() {
      var result = []
      // we need to find biggest number in array becouse that is our biggest divider
      var biggestNumber = Math.max.apply(null, this.arraySumOfDivided.map(Math.abs))

      // we are making empty array which represents all numbers available from 0 to biggestNumber
      // so we can mark numbers where we have found its prime numbers
      var marked = Array(biggestNumber + 1)

      // start looping from 2 becouse thats minimum posible prime number
      // end looping at biggest number becouse thats maximum posible prime number
      for (var i = 2; i <= biggestNumber; i++) {
        // we are skiping this step only if our divider is appearing first time as prime number
        // if divider appear as prime number at least once, we already marked all numbers where it can appear (line 733)
        if(marked[i]) continue;

        // sum of elements where prime number = i
        var sumFactors = 0
        // used to check if we increased sum 
        // if true add element to array, if false skip
        var primeExist = false

        // looping through our array and checking if element is divisible
        // if element is divisible we increase sum by its value, if not we skip
        this.arraySumOfDivided.forEach((n) => {
          if (n % i == 0) {
            sumFactors += n
            primeExist = true
          }
        })

        if (primeExist) {
          result.push([i, sumFactors])
        }

        // marking all numbers in our marked array which prime number is i
        for (var j = 2 * i; j <= biggestNumber; j += i) {
          marked[j] = true
        }
      }
      return result
    },
  },
}
</script>
<style lang="scss">
.main {
  color: #bb86fc;
  background: #121212;
  .container {
    padding: 50px;
  }

  .cards {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
    gap: 20px;
  }

  .card {
    background: #1f1f1f;
    border-radius: 10px;
    padding: 24px;
    max-width: 500px;
    transition: ease-in 0.4s all;
    border: 1px solid transparent;

    &:hover {
      transition: ease-in 0.4s all;
      border: 1px solid #bb86fc;
    }

    &.card-active {
      transition: ease-in 0.4s all;
      border: 1px solid #bb86fc;
    }
    &-flex {
      display: flex;
      align-items: center;
      gap: 20px;
      &.card-flex__col {
        flex-direction: column;
      }
    }
    .title {
      padding-bottom: 10px;
    }

    .description {
      padding-bottom: 24px;
      line-height: 22px;
      color: #b2bac2;
      transition: ease-in 0.4s all;
    }

    input {
      border: 1px solid #bb86fc;
      background: #373737;
      padding: 8px;
      height: 24px;
      border-radius: 8px;
      color: #b2bac2;
      &:focus {
        outline-width: 0;
      }
    }
  }
}
</style>
