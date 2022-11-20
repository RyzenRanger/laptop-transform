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
    <div class = "laptop">
      <div class="laptop__top">
        <img src = "@/assets/img/screen.png" alt="">
      </div>
      <div class="laptop__bottom">
        <img src = "@/assets/img/keyboard.png" alt="">
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
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
  .welcome-container {
    padding-top: 15%;
    display: flex;
    flex-direction: column;
    align-items: center;
    a {
      padding-bottom: 26px;
      img {
        width: 320px;
        border-radius: 50%;
        transition: 0.3s ease-in-out;
        &:hover {
          box-shadow: 0px 5px 10px $color-white;
        }
      }
    }
    &__text {
      margin: 0 auto;
      width: 80%;
      display: flex;
      justify-content: center;
      &--title {
        font-size: 34px;
        width: 40%;
        font-weight: bold;
      }
      &--desc {
        background-image: linear-gradient(45deg, #8bee77, #df5ec3);
        background-clip: text;
        -webkit-text-fill-color: transparent;
        font-size: 22px;
        width: 40%;
      }
    }
  }
  .laptop {
    width: 100%;
    margin: 0 auto;
    perspective: 4200px;
    perspective-origin: 50% 100%;
    transform-style: preserve-3d;
    overflow: hidden;
    img {
      width: 100%;
    }
    &__top {
      transform: rotateX(-104deg);
      transform-origin: center bottom;
    }
    &__bottom {
      margin-top: -5px;
    }
  }
}
</style>
