<template>
  <div class="main">
    <div class="container">
      <Profile/>
      <div class="cards">
        <div v-for="task in tasks" :key="task.id">
          <Task
            :id="task.id"
            :inputs="task.inputs"
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
    Profile
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
          array: [],
          method: 'spinWords',
          description:
            'Write a function that takes in a string of one or more words, and returns the same string, but with all five or more letter words reversed(Just like the name of this Kata). Strings passed in will consist of only letters and spaces. Spaces will be included only when more than one word is present.',
        },
        {
          id: '52fba66badcd10859f00097e',
          inputs: 1,
          array: [],
          method: ['disemvowel'],
          description: `Trolls are attacking your comment section! A common way to deal with this situation is to remove all of the vowels from the trolls' comments, neutralizing the threat. Your task is to write a function that takes a string and return a new string with all vowels removed. For example, the string "This website is for losers LOL!" would become "Ths wbst s fr lsrs LL!". Note: for this kata y isn't considered a vowel.`,
        },
        {
          id: '54bf1c2cd5b56cc47f0007a1',
          inputs: 1,
          array: [],
          method: ['duplicateCount'],
          description: '',
        },
        {
          id: '54c27a33fb7da0db0100040e',
          inputs: 1,
          array: [],
          method: ['isSquare'],
          description: '',
        },
        {
          id: '56606694ec01347ce800001b',
          inputs: 3,
          array: [],
          method: ['isTriangle'],
          description: '',
        },
        {
          id: '520b9d2ad5c005041100000f',
          inputs: 1,
          array: [],
          method: ['pigIt'],
          description: '',
        },
        {
          id: '541c8630095125aba6000c00',
          inputs: 1,
          array: [],
          method: ['digitalRoot'],
          description: '',
        },
        {
          id: '54e6533c92449cc251001667',
          inputs: 1,
          array: [],
          method: ['uniqueInOrder'],
          description: '',
        },
        {
          id: '554ca54ffa7d91b236000023',
          inputs: 1,
          array: [],
          method: ['deleteNth'],
          description: '',
        },
        {
          id: '5552101f47fc5178b1000050',
          inputs: 2,
          array: [],
          method: ['digPow'],
          description: '',
        },
        {
          id: '55bf01e5a717a0d57e0000ec',
          inputs: 1,
          array: [],
          method: ['persistence'],
          description: '',
        },
        {
          id: '56a5d994ac971f1ac500003e',
          inputs: 1,
          array: [],
          method: ['longestConsec'],
          description: '',
        },
        {
          id: '57b06f90e298a7b53d000a86',
          inputs: 1,
          array: [],
          method: ['queueTime'],
          description: '',
        },
        {
          id: '52f787eb172a8b4ae1000a34',
          inputs: 1,
          array: [],
          method: ['zeros'],
          description: '',
        },
        {
          id: '54d496788776e49e6b00052f',
          inputs: 1,
          array: [],
          method: ['sumOfDivided'],
          description: '',
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
  }

  .card {
    background: #1f1f1f;
    border-radius: 10px;
    padding: 24px;
    max-width: 1000px;
    transition: ease-in 0.4s all;
    border: 1px solid transparent;

    .card-stats {
      display: flex;
      align-items: center;
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
      align-items: center;
      gap: 20px;
      &.card-flex__col {
        flex-direction: column;
      }
    }

    &-header {
      display: flex;
      align-items: center;
      gap: 20px;
      padding-bottom: 10px;

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
      height: 24px;
      border-radius: 8px;
      color: #b2bac2;
      &:focus {
        outline-width: 0;
      }
    }

    &-footer {
      display: flex;
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
          background: lighten($color: rgb(31,31,31), $amount: 10%);
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
