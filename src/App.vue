<template>
  <div id = "app">
    <div class = "welcome-container">
      <a href = "https://github.com/RyzenRanger" target = "_blank">
        <img src="https://avatars.githubusercontent.com/RyzenRanger" alt="RyzenRanger">
      </a>
      <div class = "welcome-container__text">
        <p class = "welcome-container__text--title">
          What is random text generator?
        </p>
        <p class = "welcome-container__text--desc">
          Random Text Generator is a web application which
          provides true random text which you can use in your
          documents or web designs. <br /> How does it work?  <br /> First we
          took many books available on project Gutenberg and stored
          their contents in a database. <br /> Then a computer algorithm
          takes the words we stored earlier and shuffles them into
          sentences and paragraphs.
        </p>
      </div>
    </div>
    <div class = "under-laptop-container">
      <vue-typer
        class              = 'under-laptop-container--title'
        :text              = '["Hello, my dear guest 🖖"]'
        :repeat            = 'Infinity'
        :shuffle           = 'false'
        initial-action     = 'typing'
        :pre-type-delay    = '70'
        :type-delay        = '70'
        :pre-erase-delay   = '2000'
        :erase-delay       = '250'
        erase-style        = 'clear'
        :erase-on-complete = 'false'
        caret-animation    = 'expand'
      />
      <img
        class = "under-laptop-container--okay"
        src   = "@/assets/img/OK-hand.png"
        alt   = "OK"
      >
    </div>
    <div class = "laptop">
      <div
        class  = "laptop__top"
        :style = "{
          'transform': `rotateX(-${rectangleX}deg)`
          }"
      >
        <img
          v-if = "laptopIsOpen"
          src  = "@/assets/img/lt-screen.png"
          alt  = "screen-open"
        >
        <img
          src = "@/assets/img/lt-closed.png"
          alt = "sceen close"
          v-else
        >
      </div>
      <div class = "laptop__bottom">
        <img src = "@/assets/img/lt-keyboard.png" alt = "keyboard">
      </div>
    </div>
    <div class = "information-container">
      <p>Is post each that just leaf no. He connection 
        interested so we an sympathize advantages. To said 
        is it shed want do. Occasional middletons everything 
        so to. Have spot part for his quit may. Enable it is 
        square my an regard. Often merit stuff first oh up hills 
        as he. And this is some text from our generator.
      </p>
      <p><img src = "@/assets/img/web-development.png" alt = "laptop-prog">As you can easily notice the second block of text 
        looks more realistic. This way when you show a design 
        to a client you can have a result that resembles the 
        final product. However you can also use this text when 
        you need meaningless text in the background of a design 
        for a poster, t-shirt or whatever else you please.
      </p>
      <p>As you can easily notice the second block of
        text looks more realistic. This way when you
        show a design to a client you can have a
        result that resembles the final product.
        However you can also use this text when you
        need meaningless text in the background of a
        design for a poster, t-shirt or whatever else
        you please.
      </p>
      <p>Is post each that just leaf no. He connection 
        interested so we an sympathize advantages. To said 
        is it shed want do. Occasional middletons everything 
        so to. Have spot part for his quit may. Enable it is 
        square my an regard. Often merit stuff first oh up hills 
        as he. And this is some text from our generator.
      </p>
    </div>
  </div>
</template>

<script>
import { VueTyper } from 'vue-typer'

export default {
  name: 'App',

  components: {
    'vue-typer': VueTyper,
  },

  data: () => ({
    scrollY: 0,
    laptopIsOpen: true,
    windowWidth: 0,
  }),

  created() {
    this.windowWidth = window.innerWidth;
    window.addEventListener('scroll', () => {
      //432 for 768 and more
      console.log(window.scrollY)
      if (this.windowWidth >= 375) {
        if (window.scrollY <= 528) {
          this.scrollY = window.scrollY;
        } else {
          this.scrollY = 528
        }
      }

      this.checkAndChangeLaptopStatus(this.scrollY)
    })
  },

  computed: {
    rectangleX () {
      return Number(this.scrollY / 5)
    }
  },

  methods: {
    checkAndChangeLaptopStatus (scroll) {
      if (scroll >= 470) {
        this.laptopIsOpen = false;
      } else {
        this.laptopIsOpen = true;
      }
    }
  }
}
</script>

<style lang = "scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Cera Pro Medium';
}

body {
  color: $color-white;
  background-color: $color-dark;
}

#app {
  position: relative;
  .welcome-container {
    padding: 30px 0;
    display: flex;
    flex-direction: column;
    align-items: center;
    a {
      padding-bottom: 26px;
      img {
        width: 220px;
        border-radius: 50%;
        transition: 0.3s ease-in-out;
        &:hover {
          box-shadow: 0px 5px 10px $color-white;
        }
      }
    }
    &__text {
      margin: 0 auto;
      display: flex;
      flex-direction: column;
      &--title {
        max-width: 307px;
        font-size: 34px;
        font-weight: bold;
        margin-bottom: 6px;
      }
      &--desc {
        max-width: 307px;
        background-image: linear-gradient(45deg, #8bee77, #df5ec3);
        background-clip: text;
        -webkit-text-fill-color: transparent;
        font-size: 18px;
      }
    }
  }
  .under-laptop-container {
    margin: 0 auto;
    padding: 100px 0 300px;
    max-width: 900px;
    display: flex; flex-direction: column;
    align-items: center;
    &--title {
      font-size: 50px;
      margin-bottom: 24px;
    }
    &--okay {
      max-width: 300px;
    }
    @media screen and (max-width: 1299px) and (min-width: 768px) {
      padding: 60px 0 200px;
      max-width: 600px;
      &--title {
        font-size: 40px;
      }
      &--okay {
        max-width: 200px;
      }
    }
    @media screen and (max-width: 767px) and (min-width: 375px) {
      padding: 40px 0 100px;
      max-width: 307px;
      &--title {
        font-size: 20px;
        margin-bottom: 6px;
      }
      &--okay {
        max-width: 75px;
      }
    }
  }
  .laptop {
    z-index: 99999;
    position: absolute;
    padding-top: 30px;
    top: 700px;
    left: 0; right: 0;
    width: 100%;
    perspective: 2400px; //z-perspective
    perspective-origin: 48% 100%;
    transform-style: preserve-3d;
    overflow: hidden;
    display: flex; flex-direction: column;
    align-items: center;
    @media screen and (max-width: 1600px) and (min-width: 1300px) {
      perspective-origin: 46% 100%;
    }
    @media screen and (max-width: 1299px) and (min-width: 768px) {
      perspective: 1500px; //z-perspective
    }
    @media screen and (max-width: 767px) and (min-width: 375px) {
      top: 650px;
      perspective: 750px;
    }
    img {
      width: 100%;
    }
    &__top {
      margin-left: -20px;
      // transform: rotateX(0deg);
      transform-origin: center bottom;
      @media screen and (max-width: 1299px) and (min-width: 768px) {
        max-width: 550px;
        margin-left: -10px;
      }
      @media screen and (max-width: 767px) and (min-width: 375px) {
        max-width: 268px;
        width: 268px;
        margin-left: -5px;
      }
    }
    &__bottom {
      @media screen and (max-width: 1299px) and (min-width: 768px) {
        max-width: 775px;
      }
      @media screen and (max-width: 767px) and (min-width: 375px) {
        max-width: 375px;
      }
    }
  }
  .information-container {
    margin: 0 auto;
    max-width: 80%;
    background-image: linear-gradient(45deg, #d5eb0e, #f00ebf);
    background-clip: text;
    -webkit-text-fill-color: transparent;
    font-size: 18px;
    p {
      margin-bottom: 20px;
      img {
        max-width: 30%;
        float: right;
      }
    }
    @media screen and (max-width: 1299px) and (min-width: 768px) {
      max-width: 600px;
      p {
        margin-bottom: 40px;
      }
    }
    @media screen and (max-width: 767px) and (min-width: 375px) {
      max-width: 307px;
    }
  }
  .vue-typer {
    font-family: monospace;
  }

  .vue-typer .custom.char {
    color: $color-white;
  }
  .vue-typer .custom.char.selected {
    background-color: #264F78;
  }

  .vue-typer .custom.caret {
    width: 10px;
    background-color: #3F51B5;
  }
}
</style>
