<template>
  <div class="main">
    <div class="container">
      <Profile />
      <div class="cards">
        <div v-for="task in tasks" :key="task.id">
          <Task
            :id="task.id"
            :inputs="task.inputs"
            :inputLabel1="task.inputLabel1"
            :inputLabel2="task.inputLabel2"
            :inputLabel3="task.inputLabel3"
            :array="task.array"
            :method="task.method"
            :description="task.description"
          ></Task>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Task from '@/components/Task.vue'
import Profile from '@/components/Profile.vue'

export default {
  name: 'IndexPage',
  components: {
    Task,
    Profile,
  },
  head() {
    return {
      link: [
        // Add this
        {
          rel: 'stylesheet',
          href: 'https://fonts.googleapis.com/icon?family=Material+Icons',
        },
      ],
    }
  },
  data() {
    return {
      tasks: [
        {
          id: '5264d2b162488dc400000001',
          inputs: 1,
          inputLabel1: 'Enter string:',
          array: [],
          method: 'spinWords',
          description:
            'Write a function that takes in a string of one or more words, and returns the same string, but with all five or more letter words reversed(Just like the name of this Kata). Strings passed in will consist of only letters and spaces. Spaces will be included only when more than one word is present.',
        },
        {
          id: '52fba66badcd10859f00097e',
          inputs: 1,
          inputLabel1: 'Enter string:',
          array: [],
          method: 'disemvowel',
          description: `Trolls are attacking your comment section! A common way to deal with this situation is to remove all of the vowels from the trolls' comments, neutralizing the threat. Your task is to write a function that takes a string and return a new string with all vowels removed. For example, the string "This website is for losers LOL!" would become "Ths wbst s fr lsrs LL!". Note: for this kata y isn't considered a vowel.`,
        },
        {
          id: '54bf1c2cd5b56cc47f0007a1',
          inputs: 1,
          inputLabel1: 'Enter string:',
          array: [],
          method: 'duplicateCount',
          description:
            'Count the number of Duplicates. Write a function that will return the count of distinct case-insensitive alphabetic characters and numeric digits that occur more    than once in the input string. The input string can be assumed to contain only alphabets (both uppercase and lowercase) and numeric digits.',
        },
        {
          id: '54c27a33fb7da0db0100040e',
          inputs: 1,
          inputLabel1: 'Enter integer:',
          array: [],
          method: 'isSquare',
          description: `Given an integral number, determine if it's a square number: In mathematics, a square number or perfect square is an integer that is the square of an integer; in other words, it is the product of some integer with itself. The tests will always use some integral number, so don't worry about that in dynamic typed languages.`,
        },
        {
          id: '56606694ec01347ce800001b',
          inputs: 3,
          inputLabel1: 'Enter a:',
          inputLabel2: 'Enter b:',
          inputLabel3: 'Enter c:',
          array: [],
          method: 'isTriangle',
          description:
            'Implement a function that accepts 3 integer values a, b, c. The function should return true if a triangle can be built with the sides of given length and false in any other case. (In this case, all triangles must have surface greater than 0 to be accepted).',
        },
        {
          id: '520b9d2ad5c005041100000f',
          inputs: 1,
          inputLabel1: 'Enter string:',
          array: [],
          method: 'pigIt',
          description:
            'Move the first letter of each word to the end of it, then add "ay" to the end of the word. Leave punctuation marks untouched.',
        },
        {
          id: '541c8630095125aba6000c00',
          inputs: 1,
          inputLabel1: 'Enter integer:',
          array: [],
          method: 'digitalRoot',
          description:
            'Digital root is the recursive sum of all the digits in a number. Given n, take the sum of the digits of n. If that value has more than one digit, continue reducing in this way until a single-digit number is produced. The input will be a non-negative integer.',
        },
        {
          id: '54e6533c92449cc251001667',
          inputs: 1,
          inputLabel1: 'Enter string:',
          array: [],
          method: 'uniqueInOrder',
          description:
            'Implement the function unique_in_order which takes as argument a sequence and returns a list of items without any elements with the same value next to each other and preserving the original order of elements.',
        },
        {
          id: '554ca54ffa7d91b236000023',
          inputs: 1,
          inputLabel1: 'Enter integer:',
          array: [1, 2, 3, 1, 2, 1, 2, 3],
          method: 'deleteNth',
          description:
            'Given a list lst and a number N, create a new list that contains each number of lst at most N times without reordering. For example if N = 2, and the input is [1,2,3,1,2,1,2,3], you take [1,2,3,1,2], drop the next [1,2] since this would lead to 1 and 2 being in the result 3 times, and then take 3, which leads to [1,2,3,1,2,3].',
        },
        {
          id: '5552101f47fc5178b1000050',
          inputs: 2,
          inputLabel1: 'Enter n:',
          inputLabel2: 'Enter k:',
          array: [],
          method: 'digPow',
          description:
            'Some numbers have funny properties. For example: 695 --> 6² + 9³ + 5⁴= 1390 = 695 * 2. Given a positive integer n written as abcd... (a, b, c, d... being digits) and a positive integer p    we want to find a positive integer k, if it exists, such as the sum of the digits of n taken to the successive powers of p is equal to k * n. If it is the case we will return k, if not return -1. Note: n and p will always be given as strictly positive integers.',
        },
        {
          id: '55bf01e5a717a0d57e0000ec',
          inputs: 1,
          inputLabel1: 'Enter integer:',
          array: [],
          method: 'persistence',
          description:
            'Write a function, persistence, that takes in a positive parameter num and returns its multiplicative persistence, which is the number of times you must multiply the digits in num until you reach a single digit. For example (Input --> Output): 39 --> 3 (because 3*9 = 27, 2*7 = 14, 1*4 = 4 and 4 has only one digit)',
        },
        {
          id: '56a5d994ac971f1ac500003e',
          inputs: 1,
          inputLabel1: 'Enter k:',
          array: ['tree', 'foling', 'trashy', 'blue', 'abcdef', 'uvwxyz'],
          method: 'longestConsec',
          description:
            'You are given an array(list) strarr of strings and an integer k. Your task is to return the first longest string consisting of k consecutive strings taken in the array. n being the length of the string array, if n = 0 or k > n or k <= 0 return "" (return Nothing in Elm). Note: consecutive strings : follow one after another without an interruption',
        },
        {
          id: '57b06f90e298a7b53d000a86',
          inputs: 1,
          inputLabel1: 'Enter no of tills:',
          array: [8, 2, 5, 4, 1, 4, 3, 2],
          method: 'queueTime',
          description:
            'Here is a queue for the self-checkout tills at the supermarket. Your task is write a function to calculate the total time required for all the customers to check out!    Clarifications -> There is only ONE queue serving many tills, and The order of the queue NEVER changes, and The front person in the queue (i.e. the first element in the array/list) proceeds to a till as soon as it becomes free.',
        },
        {
          id: '52f787eb172a8b4ae1000a34',
          inputs: 1,
          inputLabel1: 'Enter integer:',
          array: [],
          method: 'zeros',
          description:
            'Write a program that will calculate the number of trailing zeros in a factorial of a given number. N! = 1 * 2 * 3 * ... * N. Be careful 1000! has 2568 digits...',
        },
        {
          id: '54d496788776e49e6b00052f',
          inputs: 0,
          array: [15, 21, 24, 30, 45],
          method: 'sumOfDivided',
          description:
            'Given an array of positive or negative integers I= [i1,..,in] you have to produce a sorted array P of the form [ [p, sum of all ij of I for which p is a prime factor (p positive) of ij] ...] P will be sorted by increasing order of the prime numbers. The final result has to be given as a string in Java, C#, C, C++ and as an array of arrays in other languages.',
        },
        {
          id: '514a024011ea4fb54200004b',
          inputs: 1,
          inputLabel1: 'Enter domain:',
          array: [],
          method: 'domainName',
          description: 'Write a function that when given a URL as a string, parses out just the domain name and returns it as a string. For example: domainName("http://github.com/carbonfive/raygun") == "github"',
        },
        {
          id: '539a0e4d85e3425cb0000a88',
          inputs: 0,
          array: [],
          method: 'addChain',
          description: `We want to create a function that will add numbers together when called in succession [add(1)(2); -> returns 3]. We also want to be able to continue to add numbers to our chain [add(1)(2)(3)(4)(5); // 15]. A single call should return the number passed in.`,
        },
      ],
    }
  },
}
</script>
<style lang="scss">
.main {
  color: #bb86fc;
  background: #121212;
  .container {
    padding: 50px;
    max-width: 1000px;
    margin: 0 auto;
  }

  .flex {
    display: flex;
  }

  .cursor-pointer {
    cursor: pointer;
  }

  .cards {
    display: flex;
    flex-wrap: wrap;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 20px;
    max-width: 100%;
  }

  .card {
    background: #1f1f1f;
    border-radius: 10px;
    padding: 24px;
    transition: ease-in 0.4s all;
    border: 1px solid transparent;
    width: 100%;
    .result {
      border: 1px solid #bb86fc;
      background: #373737;
      padding: 8px;
      font-size: 13px;
      border-radius: 8px;
      min-height: 33px;
      width: 200px;
      color: #b2bac2;
      display: flex;
      align-items: center;
    }

    .card-stats {
      display: flex;
      align-items: center;
      flex-wrap: wrap;
      gap: 15px;
      padding-bottom: 15px;
      &__item {
        display: flex;
        align-items: center;
        gap: 5px;
        color: #c9c9c9;
        transition: ease-out 0.3s all;

        span {
          font-size: 18px;
        }
        p {
          margin-top: 2px;
          font-size: 14px;
          line-height: 21px;

          .opacity-75 {
            opacity: 0.75;
            font-style: normal;
          }
        }
        &:hover {
          color: #bb86fc;
          transition: ease-in 0.3s all;
        }
      }
    }

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
      gap: 15px;
      &.card-flex__col {
        flex-direction: column;
      }
    }

    &-input__flex {
      display: flex;
      gap: 3px;
      flex-direction: column;
      label {
        font-size: 15px;
        line-height: 21px;
      }
    }

    &-header {
      display: flex;
      align-items: center;
      gap: 20px;
      padding-bottom: 10px;
      @media only screen and (max-width: 600px) {
        flex-wrap: wrap;
      }
      .ranking-inner {
        height: 22px;
        width: 32px;
        background-color: #181919;
        position: relative;
        margin-right: 6px;
        text-align: center;
        z-index: 1;
        text-shadow: none;
        margin-left: 1px;
        top: 2px;
        &:before {
          content: ' ';
          width: 0;
          height: 0;
          border-right: 6px solid #181919;
          border-top: 11px solid transparent;
          border-bottom: 11px solid transparent;
          position: absolute;
          left: -6px;
          z-index: 0;
        }
        &:after {
          content: '';
          width: 0;
          position: absolute;
          right: -6px;
          top: 0;
          border-left: 6px solid #181919;
          border-top: 11px solid transparent;
          border-bottom: 11px solid transparent;
          z-index: 0;
          -moz-transform: scale(0.9999);
          z-index: 2;
        }
      }

      .ranking-outer {
        color: #bb86fc;
        background: #bb86fc;
        font-size: 11px;
        line-height: 22px;
        font-weight: 700;
        width: 34px;
        height: 26px;
        position: relative;
        margin-right: 8px;
        margin-left: 8px;
        text-align: center;
        z-index: 1;
        text-shadow: none;
        &:before {
          content: ' ';
          width: 0;
          height: 0;
          border-right: 8px solid #bb86fc;
          border-top: 13px solid transparent;
          border-bottom: 13px solid transparent;
          position: absolute;
          left: -8px;
          z-index: -1;
          -moz-transform: scale(0.9999);
        }
        &:after {
          content: '';
          width: 0;
          position: absolute;
          right: -8px;
          top: 0;
          border-left: 8px solid #bb86fc;
          border-top: 13px solid transparent;
          border-bottom: 13px solid transparent;
          z-index: 0;
        }
      }
      .title {
        display: inline-block;
        position: relative;
        cursor: pointer;
        transition: ease-out 0.3s all;
        text-decoration: none;
        // white-space: nowrap;
        // overflow: hidden;
        // text-overflow: ellipsis;
        // max-width: 50px;
        // min-width: 90%; /*add this it*/
        @media only screen and (max-width: 600px) {
          font-size: 22px;
        }
        &:hover {
          color: darken($color: #bb86fc, $amount: 10);
          transition: ease-in 0.3s all;
        }
        &:after {
          background: none repeat scroll 0 0 transparent;
          bottom: -4px;
          content: '';
          display: block;
          height: 2px;
          left: 50%;
          position: absolute;
          background: darken($color: #bb86fc, $amount: 10);
          transition: width 0.3s ease 0s, left 0.3s ease 0s;
          width: 0;
        }
        &:hover:after {
          width: 100%;
          left: 0;
        }
      }
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
      height: 33px;
      border-radius: 8px;
      width: 200px;
      color: #b2bac2;
      &:focus {
        outline-width: 0;
      }
    }

    &-footer {
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      gap: 20px;
      color: #efefef;
      text-transform: uppercase;
      padding-top: 20px;
      span {
        font-size: 18px;
      }
      &__tag {
        display: flex;
        align-items: center;
        gap: 8px;
        color: #efefef;
        transition: ease-out 0.3s all;

        p {
          margin-top: 2px;
          font-size: 10px;
          line-height: 21px;
          display: inline-block;
          border-radius: 4px;
          letter-spacing: 0.4px;
          padding: 1px 6px;
          background: lighten($color: rgb(31, 31, 31), $amount: 10%);
        }
        &:hover {
          color: #bb86fc;
          transition: ease-in 0.3s all;
        }
      }
    }
  }
}
</style>
