<template lang="pug">
main.v-oogle
  section.logo-box(:class="{ 'move-up': inputFocused }")
    .img
      a(href="https://github.com/VeryWow/v-oogle")
        img(
        alt="V-oogle"
        title="Because why not?"
        width="272"
        height="84"
        :src="logo")
  section.search-box
    search-input.search(@focus="inputFocused = true", @blur="inputFocused = false")
</template>

<script lang="ts">
  import SearchInput from 'components/SearchInput.vue'

  import Vue from 'vue'
  export default Vue.extend({
    components: {
      SearchInput
    },
    data: () => ({
      inputFocused: false
    }),
    computed: {
      logo() {
        return require('~/v-oogle.png');
      }
    }
  })
</script>

<style lang="scss">
* {
  box-sizing: border-box;
  font-family: arial,sans-serif;
}

.v-oogle {
  .logo-box {
    margin-top: 89px;
    text-align: center;

    .img {
      user-select: none;
      padding-top: 109px;
      display: block;
      margin: 0 auto;
      width: 272px;

      img {
        display: block;
      }
    }
  }

  .search-box {
    margin-top: 28px;
    .search {
      width: 484px;
      margin: 0 auto;
    }
  }
}

@media screen and (min-width: 1250px) {
  .v-oogle {
    .search-box {
      .search {
        width: 584px;
      }
    }
  }
}

@media screen and (min-device-width: 680px) {
  html {
    min-width: 980px;
  }
}

@media screen and (max-device-width: 679px) {
  html {
    padding: 10px;
  }
  .v-oogle {
    .logo-box {
      margin-top: 0;
      transition: margin .15s ease;

      .img {
        padding-top: 40px;
      }

      &.move-up {
        margin-top: -152px;
      }
    }
    .search-box {
      .search {
        width: 100%;
      }
    }
  }
}
</style>
