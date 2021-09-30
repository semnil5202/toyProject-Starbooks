<template>
  <div class="swiper-container">
    <div
      class="swiper-wrapper">
      <div
        class="swiper-slide">
        <RouterLink
          :to="`/DetailedBook/${homeBooks1.id}`"
          class="book-zone">
          <div
            class="bookImage"
            :style="{backgroundImage: `url(${requestDiffSizeImage(homeBooks1.imgUrl)})`}">
          </div>
          <div class="book-detail">
            <p class="book-title">
              {{ homeBooks1.title }}
            </p>
            <p class="book-author">
              {{ homeBooks1.author }}
            </p>
            <p class="book-description">
              {{ homeBooks1.publisher }}
            </p>
          </div>
        </RouterLink>
      </div>
      <div
        class="swiper-slide">
        <RouterLink
          :to="`/DetailedBook/${homeBooks2.id}`"
          class="book-zone">
          <div
            class="bookImage"
            :style="{backgroundImage: `url(${requestDiffSizeImage(homeBooks2.imgUrl)})`}">
          </div>
          <div class="book-detail">
            <p class="book-title">
              {{ homeBooks2.title }}
            </p>
            <p class="book-author">
              {{ homeBooks2.author }}
            </p>
            <p class="book-description">
              {{ homeBooks2.publisher }}
            </p>
          </div>
        </RouterLink>
      </div>
      <div
        class="swiper-slide">
        <RouterLink
          :to="`/DetailedBook/${homeBooks3.id}`"
          class="book-zone">
          <div
            class="bookImage"
            :style="{backgroundImage: `url(${requestDiffSizeImage(homeBooks3.imgUrl)})`}">
          </div>
          <div class="book-detail">
            <p class="book-title">
              {{ homeBooks3.title }}
            </p>
            <p class="book-author">
              {{ homeBooks3.author }}
            </p>
            <p class="book-description">
              {{ homeBooks3.publisher }}
            </p>
          </div>
        </RouterLink>
      </div>
      <div
        class="swiper-slide">
        <RouterLink
          :to="`/DetailedBook/${homeBooks4.id}`"
          class="book-zone">
          <div
            class="bookImage"
            :style="{backgroundImage: `url(${requestDiffSizeImage(homeBooks4.imgUrl)})`}">
          </div>
          <div class="book-detail">
            <p class="book-title">
              {{ homeBooks4.title }}
            </p>
            <p class="book-author">
              {{ homeBooks4.author }}
            </p>
            <p class="book-description">
              {{ homeBooks4.publisher }}
            </p>
          </div>
        </RouterLink>
      </div>
      <div
        class="swiper-slide">
        <RouterLink
          :to="`/DetailedBook/${homeBooks5.id}`"
          class="book-zone">
          <div
            class="bookImage"
            :style="{backgroundImage: `url(${requestDiffSizeImage(homeBooks5.imgUrl)})`}">
          </div>
          <div class="book-detail">
            <p class="book-title">
              {{ homeBooks5.title }}
            </p>
            <p class="book-author">
              {{ homeBooks5.author }}
            </p>
            <p class="book-description">
              {{ homeBooks5.publisher }}
            </p>
          </div>
        </RouterLink>
      </div>
    </div>
  </div>

  <div class="topic-container">
    <div class="topic-section">
      <h2 class="topic-section-name">
        오늘, <span class="star">STAR</span> 의 발견
      </h2>
      <div class="topic-cell">
        <HomeBookItemStar
          v-for="book in searchHomeBooksIdStar"
          :key="book.isbn"
          :book="book" />
      </div>
    </div>
  </div>

  <div class="hot-container">
    <div class="hot-section">
      <h2 class="hot-section-name">
        지금, <span class="hot">HOT</span> 한 책
      </h2>
      <div class="hot-cell">
        <HomeBookItemHot
          v-for="book in searchHomeBooksIdHot"
          :key="book.isbn"
          :book="book" />
      </div>
    </div>
  </div>
</template>

<script>
import HomeBookItemStar from '~/components/HomeBookItemStar'
import HomeBookItemHot from '~/components/HomeBookItemHot'

export default {
  components: {
    HomeBookItemStar,
    HomeBookItemHot
  },
  data() {
    return {
    }
  },
  computed: {
    homeBooks1() {
      return this.$store.state.book.homeBooks1
    },
    homeBooks2() {
      return this.$store.state.book.homeBooks2
    },
    homeBooks3() {
      return this.$store.state.book.homeBooks3
    },
    homeBooks4() {
      return this.$store.state.book.homeBooks4
    },
    homeBooks5() {
      return this.$store.state.book.homeBooks5
    },
    searchHomeBooksIdStar() {
      return this.$store.state.book.searchHomeBooksIdStar
    },
    searchHomeBooksIdHot() {
      return this.$store.state.book.searchHomeBooksIdHot
    }
  },
  async created () {
    this.$store.dispatch('book/homeBooks1', {
      id: 2
    })
    this.$store.dispatch('book/homeBooks2', {
      id: 38
    })
    this.$store.dispatch('book/homeBooks3', {
      id: 120
    })
    this.$store.dispatch('book/homeBooks4', {
      id: 90
    })
    this.$store.dispatch('book/homeBooks5', {
      id: 109
    })
    this.$store.dispatch('book/searchHomeBooksIdStar', {
      page: 14,
      size: 6
    })
    this.$store.dispatch('book/searchHomeBooksIdHot', {
      page: 28,
      size: 8
    })
  },
  methods: {
    requestDiffSizeImage(url, imgSize = "xxlarge") {
      return url.replace('large', `${imgSize}`)
    }
  },
}
</script>

<style lang="scss" scoped>
@import "~/scss/main";

.swiper-container {
  border-top: solid 1px #ebebeb;
  border-bottom: solid 1px #ebebeb;
  margin-top: 80px;
  padding: 0;
  width: 1280px;
  height: 300px;
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
  left: 0;
  right: 0;
  margin-left: auto;
  margin-right: auto;
  .swiper-wrapper {
    padding: 0;
    width: 1260px;
    height: 280px;
    position: absolute;

    //slide
    white-space: nowrap;
    .swiper-slide {
      padding: 0;
      margin-right: 8px;
      width: 420px;
      height: 280px;
      display: inline-block;
      background-color: #ebebeb;
      .bookImage{
        width: 280px;
        height: 280px;
        background-size: contain;
        background-repeat: no-repeat;
      }
    }
  }
}

.topic-container {
  padding: 0;
  margin-top: 180px;
  width: 1200px;
  height: 420px;
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
  left: 0;
  right: 0;
  margin-left: auto;
  margin-right: auto;
  .topic-section {
    padding: 0;
    width: 1200px;
    height: 400px;
    justify-content: center;
    overflow: hidden;
    position: absolute;
    .topic-section-name {
      &:after {
        content: "";
        margin-top: 1px;
        display: block;
        width: 1176px;
        border-bottom: solid 1px #ebebeb;
      }
      margin-bottom: 20px;
      padding-left: 24px;
      font-size: 24px;
      font-weight: 700;
      font-family: sans-serif;
      word-spacing: -4px;
      .star {
        color: #ffc107;
        -webkit-text-stroke: 0.5px $primary;
      }
    }
    .topic-cell {
      display: flex
    }
  }
}

.hot-container {
  padding: 0;
  margin-top: 40px;
  width: 1200px;
  height: 520px;
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
  left: 0;
  right: 0;
  margin-left: auto;
  margin-right: auto;
  .hot-section {
    padding: 0;
    width: 1200px;
    height: 500px;
    justify-content: center;
    overflow: hidden;
    position: absolute;
    .hot-section-name {
      &:after {
        content: "";
        margin-top: 1px;
        display: block;
        width: 1176px;
        border-bottom: solid 1px #ebebeb;
      }
      margin-bottom: 20px;
      padding-left: 24px;
      font-size: 24px;
      font-weight: 700;
      font-family: sans-serif;
      word-spacing: -4px;
      .hot{
        color: rgb(245, 76, 76);
        -webkit-text-stroke: 0.5px $primary;
      }
    }
    .hot-cell{
      display: flex;
      flex-wrap: wrap;
    }
  }
}
</style>