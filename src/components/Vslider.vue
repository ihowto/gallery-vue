<template>
  <div style="width: 90%">
    <div @mouseenter="enter" @mouseleave="leave">
      <transition name="fade" mode="out-in">
        <div :style="backgourndImg" :key="currentIndex"></div>
      </transition>
      <p class="introduction">{{items[currentIndex].discription}}</p>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'hello',
    data () {
      return {
        items: [
          {
            image: 'http://gallery-1253482132.cossh.myqcloud.com/img/wimg1.jpg',
            discription: '来自吷买井页的Gallery'
          },
          {
            image: 'http://gallery-1253482132.cossh.myqcloud.com/img/wimg2.jpg',
            discription: 'ようこそGallery'
          },
          {
            image: 'http://gallery-1253482132.cossh.myqcloud.com/img/wimg3.jpg',
            discription: 'From Howto\'s Gallery'
          },
          {
            image: 'http://gallery-1253482132.cossh.myqcloud.com/img/wimg4.jpg',
            discription: 'Bienvenue à la galerie'
          }
        ],
        currentIndex: 0,
        timerId: 0
      }
    },
    methods: {
      add: function () {
        if (this.currentIndex < 2) {
          ++this.currentIndex
        } else {
          this.currentIndex = 0
        }
      },
      enter: function () {
        clearInterval(this.timerId)
      },
      leave: function () {
        this.add()
        this.timerId = setInterval(this.add, 3000)
      }
    },
    computed: {
      backgourndImg: function () {
        return {
          width: '100%',
          height: '600px',
          background: 'url(' + this.items[this.currentIndex].image + ')',
          backgroundSize: 'cover'
        }
      }
    },
    created: function () {
      this.timerId = setInterval(this.add, 3000)
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .fade-enter-active, .fade-leave-active {
    transition: opacity .5s
  }
  .fade-enter, .fade-leave-to /* .fade-leave-active in below version 2.1.8 */ {
    opacity: 0
  }
  .introduction {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: left;
    color: black;
    font-weight: 500;
  }
</style>
