<template>
  <div class="card" :class="{ 'card-active': taskActive }">
    <div class="card-header">
      <div class="ranking-outer">
        <div class="ranking-inner">
          {{ task.rank['name'] }}
        </div>
      </div>
      <h1 @click="openLink(task.url)" class="title">{{ task.name }}</h1>
    </div>
    <div class="card-stats">
      <div class="card-stats__item">
        <span class="material-icons">star_border</span>
        <p>{{ task.totalStars }}</p>
      </div>
      <div class="card-stats__item">
        <span class="material-icons">thumb_up_off_alt</span>
        <p>{{ task.voteScore }}</p>
      </div>
      <div class="card-stats__item">
        <span class="material-icons">track_changes</span>
        <p>
          {{ task.totalCompleted }} <i class="opacity-75">of</i>
          {{ task.totalAttempts }}
        </p>
      </div>
      <div class="card-stats__item">
        <span class="material-icons">person_outline</span>
        <p class="cursor-pointer" @click="openLink(task.createdBy['url'])">
          {{ task.createdBy['username'] }}
        </p>
      </div>
    </div>
    <p class="description">
      {{ description }}
    </p>
    <div class="card-flex card-flex__col">
      <div v-if="array.length" class="card-input__flex">
        <label>Array:</label>
        <p class="result">{{ array }}</p>
      </div>
      <div class="card-input__flex" v-if="method === 'functionCalculating'">
        <label>Input:</label>
        <p class="result">two(minus(seven()))</p>
      </div>
      <div class="card-input__flex" v-else-if="method === 'addChain'">
        <label>Input:</label>
        <p class="result">addChain(1)(2)(3)(4)(5)</p>
      </div>
      <div v-if="inputs === 1" class="card-input__flex">
        <label>{{ inputLabel1 }}</label>
        <input
          v-model="input1"
          @focus="taskActive = true"
          @blur="taskActive = false"
        />
      </div>
      <div v-if="inputs === 2" class="card-flex card-flex__col">
        <div class="card-input__flex">
          <label>{{ inputLabel1 }}</label>
          <input
            v-model="input1"
            @focus="taskActive = true"
            @blur="taskActive = false"
          />
        </div>
        <div class="card-input__flex">
          <label>{{ inputLabel2 }}</label>
          <input
            v-model="input2"
            @focus="taskActive = true"
            @blur="taskActive = false"
          />
        </div>
      </div>
      <div v-if="inputs === 3" class="card-flex card-flex__col">
        <div class="card-input__flex">
          <label>{{ inputLabel1 }}</label>
          <input
            v-model="input1"
            @focus="taskActive = true"
            @blur="taskActive = false"
          />
        </div>
        <div class="card-input__flex">
          <label>{{ inputLabel2 }}</label>
          <input
            v-model="input2"
            @focus="taskActive = true"
            @blur="taskActive = false"
          />
        </div>
        <div class="card-input__flex">
          <label>{{ inputLabel3 }}</label>
          <input
            v-model="input3"
            @focus="taskActive = true"
            @blur="taskActive = false"
          />
        </div>
      </div>
      <div v-if="inputs === 0" class="card-input__flex">
        <div class="card-input__flex" v-if="method === 'functionCalculating'">
          <label>Result:</label>
          <p class="result">{{ two(minus(seven())) }}</p>
        </div>
        <div class="card-input__flex" v-else-if="method === 'addChain'">
          <label>Result:</label>
          <p class="result">{{ addChain(1)(2)(3)(4)(5) }}</p>
        </div>
        <div v-else>
          <label>Result:</label>
          <p class="result">{{ callMethod(method) }}</p>
        </div>
      </div>
      <div v-if="inputs === 1" class="card-input__flex">
        <label>Result:</label>
        <p class="result" v-if="input1">{{ callMethod(method, input1) }}</p>
        <p class="result" v-if="!input1"></p>
      </div>
      <div v-if="inputs === 2" class="card-input__flex">
        <label>Result:</label>
        <p class="result" v-if="input1 && input2">
          {{ callMethod(method, input1, input2) }}
        </p>
        <p class="result" v-if="!input1 || !input2"></p>
      </div>
      <div v-if="inputs === 3" class="card-input__flex">
        <label>Result:</label>
        <p class="result" v-if="input1 && input2 && input3">
          {{ callMethod(method, input1, input2, input3) }}
        </p>
        <p class="result" v-if="!input1 || !input2 || !input3"></p>
      </div>
    </div>
    <div class="card-footer">
      <span class="material-icons"> loyalty </span>
      <div v-for="item in filteredTags" :key="item" class="card-footer__tag">
        <p>{{ item }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      task: [],
      taskActive: false,
      input1: '',
      input2: '',
      input3: '',
    }
  },
  props: {
    id: {
      type: [String],
    },
    inputs: {
      type: [Number],
    },
    inputLabel1: {
      type: [String],
    },
    inputLabel2: {
      type: [String],
    },
    inputLabel3: {
      type: [String],
    },
    array: {
      type: [Array],
    },
    method: {
      type: [String],
    },
    description: {
      type: [String],
    },
  },
  async fetch() {
    this.task = await fetch(
      `https://www.codewars.com/api/v1/code-challenges/${this.id}`
    ).then((res) => res.json())
  },
  computed: {
    filteredTags() {
      return this.task.tags.slice(0, 3)
    },
  },
  methods: {
    // Call methods
    callMethod(method, arg1, arg2, arg3) {
      if (this.inputs === 1) {
        return this[method](arg1)
      } else if (this.inputs === 2) {
        console.log('????', this.inputs.length)
        return this[method](arg1, arg2)
      } else if (this.inputs === 3) {
        return this[method](arg1, arg2, arg3)
      }
      return this[method]()
    },

    // Open link
    openLink(url) {
      window.open(url, '_blank')
    },

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
      var arr = [...this.array]
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
        console.log(item, 'pa', sum)
        console.log('item =>', parseInt(item))
        console.log('pow =>', pow)
        sum = sum + Math.pow(parseInt(item), pow)
        pow++
      })
      n = n.join('')
      // if sum equal original number is equal is integer
      // we return that number
      // else return -1
      console.log(sum, 'pa', n)
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

      if (this.array.length === 0 || k > this.array.length || k <= 0)
        return 'Try another number.'
      var result = ''
      for (let i = 0; i <= this.array.length - k; i++) {
        var str = ''
        for (let j = i; j < i + k; j++) {
          str += this.array[j]
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

      // array that represents tills (every value is 0 becouse tills are empty for now)
      var arr = Array(n).fill(0)

      // looping through array of customers
      // we are adding customers queue time to the till which have lowest queue time
      // we are sorting array, so we can add next customer queue time to the lowest till (first element of array)
      for (let i = 0; i < this.array.length; i++) {
        arr[0] += this.array[i]
        arr.sort((a, b) => a - b)
      }

      // returning last element in array becouse it contains max queue time
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
      var biggestNumber = Math.max.apply(null, this.array.map(Math.abs))

      // we are making empty array which represents all numbers available from 0 to biggestNumber
      // so we can mark numbers where we have found its prime numbers
      var marked = Array(biggestNumber + 1)

      // start looping from 2 becouse thats minimum posible prime number
      // end looping at biggest number becouse thats maximum posible prime number
      for (var i = 2; i <= biggestNumber; i++) {
        // we are skiping this step only if our divider is appearing first time as prime number
        // if divider appear as prime number at least once, we already marked all numbers where it can appear (line 733)
        if (marked[i]) continue

        // sum of elements where prime number = i
        var sumFactors = 0
        // used to check if we increased sum
        // if true add element to array, if false skip
        var primeExist = false

        // looping through our array and checking if element is divisible
        // if element is divisible we increase sum by its value, if not we skip
        this.array.forEach((n) => {
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

    // Task 16

    // Write a function that when given a URL as a string, parses out just the domain name and returns it as a string.
    // For example: domainName("http://github.com/carbonfive/raygun") == "github"

    domainName(url) {
      return url
        .replace('http://', '')
        .replace('https://', '')
        .replace('www.', '')
        .split('.')[0]
    },

    // Task 17
    // This time we want to write calculations using functions and get the results.
    // Let's have a look at some examples:
    // seven(times(five())); -> must return 35
    // four(plus(nine())); -> must return 13
    // eight(minus(three())); -> must return 5
    // six(dividedBy(two())); -> must return 3

    // Explaination
    // two(plus(three()))
    // JavaScript is running from the inside 1st
    // it will try to calculate three() =>
    // next function plus will return function(a) => {a + 3}

    zero(func) {
      return func ? func(0) : 0
    },

    one(func) {
      return func ? func(1) : 1
    },

    two(func) {
      return func ? func(2) : 2
    },

    three(func) {
      return func ? func(3) : 3
    },

    four(func) {
      return func ? func(4) : 4
    },

    five(func) {
      return func ? func(5) : 5
    },

    six(func) {
      return func ? func(6) : 6
    },

    seven(func) {
      return func ? func(7) : 7
    },

    eight(func) {
      return func ? func(8) : 8
    },

    nine(func) {
      return func ? func(9) : 9
    },

    plus(b) {
      return function (a) {
        return a + b
      }
    },

    minus(b) {
      return function (a) {
        return a - b
      }
    },

    times(b) {
      return function (a) {
        return a * b
      }
    },

    dividedBy(b) {
      return function (a) {
        return a / b
      }
    },

    // Task 18

    // We want to create a function that will add numbers together when called in succession.
    // add(1)(2) -> returns 3
    // We also want to be able to continue to add numbers to our chain.
    // add(1)(2)(3)(4)(5); // returns 15
    // A single call should return the number passed in.
    // add(1) -> returns 1

    addChain(n) {
      var currentSum = n

      function f(b) {
        currentSum += b
        return f
      }

      f.toString = function () {
        return currentSum
      }

      return f
    },

    // Task 19

    // Consider a sequence u where u is defined as follows:
    // The number u(0) = 1 is the first one in u.
    // For each x in u, then y = 2 * x + 1 and z = 3 * x + 1 must be in u too.
    // There are no other numbers in u.
    // Ex: u = [1, 3, 4, 7, 9, 10, 13, 15, 19, 21, 22, 27, ...]
    // 1 gives 3 and 4, then 3 gives 7 and 10, 4 gives 9 and 13, then 7 gives 15 and 22 and so on...

    dblLinear(n) {
      // The number u(0) = 1 is the first one in u.
      // x & y = 0 so we can count nextX and nextY from the first element
      // also we are saving index of elements that were not added yet to array
      // when we add element, we increase x or y, so we can move on next element and count it nextX or nextY
      let u = [1],
        x = 0,
        y = 0

      // looping throug array from the start to the n
      for (let i = 0; i < n; i++) {
        // count nextX and nextY by given formula
        let nextX = 2 * u[x] + 1,
          nextY = 3 * u[y] + 1

        // sorting elements so we can add smaller element first
        // if nextX <= nextY, we add nextX to array and increase x index for 1
        if (nextX <= nextY) {
          u.push(nextX)
          x++
          // if nextX and nextY are same numbers, we just increase y index for 1
          // becouse we already added that number in last step
          if (nextX == nextY) y++
        } else {
          // if nextY > nextX, we add nextY to array and increase y index for 1
          u.push(nextY)
          y++
        }
      }

      // return last element of array
      return u[n]
    },

    // Task 20

    // Sort "array" so that all elements with the value of zero are moved to the
    // end of the array, while the other elements maintain order.
    // [0, 1, 2, 0, 3] --> [1, 2, 3, 0, 0]
    // Zero elements also maintain order in which they occurred.
    // [0, "0", 1, 2, 3] --> [1, 2, 3, 0, "0"]
    // Do not use any temporary arrays or objects. Additionally, you're not able
    // to use any Array or Object prototype methods such as .shift(), .push(), etc
    // the correctly sorted array should be returned.

    removeZeros() {
      // recursive helper function
      const sendToBack = (i) => {
        if (i === this.array.length - 1) return
        else {
          if (this.array[i + 1] === 0 || this.array[i + 1] === '0') return
          else {
            let temp = this.array[i]
            this.array[i] = this.array[i + 1]
            this.array[i + 1] = temp
            return sendToBack(i + 1)
          }
        }
      }
      // loop through backwards, when you hit a zero call helper
      let j = this.array.length - 1
      while (j >= 0) {
        if (this.array[j] == 0 && typeof this.array[j] !== 'boolean') {
          sendToBack(j)
        }
        j--
      }
      return this.array
    },
  },
}
</script>

<style lang="scss" scoped>
</style>