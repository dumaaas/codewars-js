<template>
  <div class="main">
    <div class="container">
      <div class="cards">
        <div class="card">
          <h1 class="title">Task 1</h1>
          <p class="description">
            Write a function that takes in a string of one or more words, and
            returns the same string, but with all five or more letter words
            reversed(Just like the name of this Kata). Strings passed in will
            consist of only letters and spaces. Spaces will be included only
            when more than one word is present.
          </p>
          <div class="card-flex">
            <input v-model="wordSpin" />
            <p v-if="wordSpin">{{ spinWords(wordSpin) }}</p>
          </div>
        </div>
        <div class="card">
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
            <input v-model="wordDisemvowel" />
            <p v-if="wordDisemvowel">{{ disemvowel(wordDisemvowel) }}</p>
          </div>
        </div>
        <div class="card">
          <h1 class="title">Task 3</h1>
          <p class="description">
            Count the number of Duplicates Write a function that will return the
            count of distinct case-insensitive alphabetic characters and numeric
            digits that occur more than once in the input string. The input
            string can be assumed to contain only alphabets (both uppercase and
            lowercase) and numeric digits.
          </p>
          <div class="card-flex">
            <input v-model="wordDuplicateCount" />
            <p v-if="wordDuplicateCount">
              {{ duplicateCount(wordDuplicateCount) }}
            </p>
          </div>
        </div>
        <div class="card">
          <h1 class="title">Task 4</h1>
          <p class="description">
            Given an integral number, determine if it's a square number: In
            mathematics, a square number or perfect square is an integer that is
            the square of an integer; in other words, it is the product of some
            integer with itself. The tests will always use some integral number,
            so don't worry about that in dynamic typed languages.
          </p>
          <div class="card-flex">
            <input v-model="wordIsSquare" />
            <p v-if="wordIsSquare">
              {{ isSquare(wordIsSquare) }}
            </p>
          </div>
        </div>
        <div class="card">
          <h1 class="title">Task 5</h1>
          <p class="description">
            Implement a function that accepts 3 integer values a, b, c. The
            function should return true if a triangle can be built with the
            sides of given length and false in any other case. (In this case,
            all triangles must have surface greater than 0 to be accepted).
          </p>
          <div class="card-flex card-flex__col">
            <input v-model="wordIsTriangleA" />
            <input v-model="wordIsTriangleB" />
            <input v-model="wordIsTriangleC" />

            <p v-if="wordIsTriangleA && wordIsTriangleB && wordIsTriangleC">
              {{
                isTriangle(wordIsTriangleA, wordIsTriangleB, wordIsTriangleC)
              }}
            </p>
          </div>
        </div>
        <div class="card">
          <h1 class="title">Task 6</h1>
          <p class="description">
            Move the first letter of each word to the end of it, then add "ay"
            to the end of the word. Leave punctuation marks untouched.
          </p>
          <div class="card-flex">
            <input v-model="wordPigIt" />
            <p v-if="wordPigIt">
              {{ pigIt(wordPigIt) }}
            </p>
          </div>
        </div>
        <div class="card">
          <h1 class="title">Task 7</h1>
          <p class="description">
            Digital root is the recursive sum of all the digits in a number.
            Given n, take the sum of the digits of n. If that value has more
            than one digit, continue reducing in this way until a single-digit
            number is produced. The input will be a non-negative integer.
          </p>
          <div class="card-flex">
            <input v-model="wordDigitalRoot" />
            <p v-if="wordDigitalRoot">
              {{ digitalRoot(wordDigitalRoot) }}
            </p>
          </div>
        </div>
        <div class="card">
          <h1 class="title">Task 8</h1>
          <p class="description">
            Implement the function unique_in_order which takes as argument a
            sequence and returns a list of items without any elements with the
            same value next to each other and preserving the original order of
            elements.
          </p>
          <div class="card-flex">
            <input v-model="wordUniqueInOrder" />
            <p v-if="wordUniqueInOrder">
              {{ uniqueInOrder(wordUniqueInOrder) }}
            </p>
          </div>
        </div>
        <div class="card">
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
            <input v-model="wordDeleteNth" />
            <p v-if="wordDeleteNth">
              {{ deleteNth(wordDeleteNth) }}
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
    }

    input {
      border: 1px solid #b2bac2;
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
