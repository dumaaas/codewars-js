<template>
  <div class="user">
    <div class="user-avatar">
      <img src="@/assets/avatar.jpg" />
    </div>
    <div class="user-main">
      <div class="user-main__name">
        <div class="name-card">
          <div class="user-main__name ml">
            <div class="card-header">
              <div class="ranking-outer">
                <div class="ranking-inner">
                  {{ user.ranks.overall['name'] }}
                </div>
              </div>
            </div>
            <p class="name">
              {{ user.username }}
            </p>
          </div>
        </div>

        <div class="honor">{{ user.honor }}</div>
      </div>
      <div class="user-main__info">
        <div class="user-main__info--col">
          <div class="user-main__info--item">
            <span>Name:</span>
            <p>{{ user.name }}</p>
          </div>
          <div class="user-main__info--item">
            <span>Country:</span>
            <p>Montenegro</p>
          </div>
          <div class="user-main__info--item">
            <span>City:</span>
            <p>Niksic</p>
          </div>
        </div>

        <div class="user-main__info--col">
          <div class="user-main__info--item">
            <span>Language:</span>
            <p>JavaScript</p>
          </div>
          <div class="user-main__info--item">
            <span>Position:</span>
            <p>{{ user.leaderboardPosition }}</p>
          </div>
        </div>
        <div class="user-main__info--col">
          <div class="user-main__info--item">
            <span>Challenges:</span>
            <p>{{ user.codeChallenges['totalCompleted'] }}</p>
          </div>
          <div class="user-main__info--item">
            <span>Profiles:</span>
            <p @click="openLink('https://github.com/dumaaas')">Github</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      user: [],
    }
  },
  async fetch() {
    this.user = await fetch(
      `https://www.codewars.com/api/v1/users/dumaaas`
    ).then((res) => res.json())
  },
  methods: {
    // Open link
    openLink(url) {
      window.open(url, '_blank')
    },
  },
}
</script>

<style lang="scss" scoped>
.user {
  background: #1d1d1f;
  display: flex;
  gap: 33px;
  padding: 15px 15px 50px 15px;
  margin-bottom: 30px;
  @media only screen and (max-width: 600px) {
    padding: 24px;
  }
  .card-header {
    padding-bottom: 0;
    padding-left: 0;
  }

  .ranking-outer {
    z-index: 3 !important;
  }

  .user-main {
    display: flex;
    flex-direction: column;
    width: 100%;
    gap: 15px;
    .honor {
      color: #b0b0b0;
      font-size: 14px;
      line-height: 21px;
    }
    &__name {
      display: flex;
      gap: 10px;
      align-items: center;

      .ml {
        margin-left: -7px;
      }

      .name-card {
        width: 263px;
        background: #303133;
        padding: 5px 0;
        position: relative;
        z-index: 1;

        &:before {
          content: ' ';
          width: 0;
          height: 0;
          border-right: 12px solid #303133;
          border-top: 18px solid transparent;
          border-bottom: 18px solid transparent;
          position: absolute;
          left: -12px;
          z-index: 2;
          top: 0px;
        }
        &:after {
          content: ' ';
          width: 0;
          height: 0;
          border-right: 12px solid rgb(29, 29, 31);
          border-top: 18px solid transparent;
          border-bottom: 18px solid transparent;
          position: absolute;
          right: 0;
          z-index: 2;
          top: 0px;
        }

        .name {
          font-size: 22px;
          line-height: 26px;
          font-weight: 600;
        }
      }
    }
    &__info {
      display: flex;
      width: 100%;
      @media only screen and (max-width: 600px) {
        flex-wrap: wrap;
      }
      &--col {
        display: flex;
        flex-direction: column;
        width: 263px;
      }
      &--item {
        display: flex;
        align-items: center;
        gap: 4px;
        font-size: 14px;
        line-height: 21px;
        span {
          color: #b0b0b0;
          font-weight: 700;
        }
        p {
          color: #efefef;
        }
      }
    }
  }
  .user-avatar {
    max-width: 75px;
    height: 75px;
    img {
      max-width: 100%;
      border-radius: 8px;
    }
    @media only screen and (max-width: 600px) {
      display: none;
    }
  }
}
</style>