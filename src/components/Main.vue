<template>
  <div class="center" v-if="!main">
    <v-btn size="x-large" absolute @click="this.clicked()" v-if="click"
      >Teste</v-btn
    >
    <div class="heart" v-if="animation"></div>
  </div>
  <div class="main" v-else>
    <Confetti />
    <h1 class="title">
      <v-icon icon="mdi-party-popper"></v-icon>21 da Júlia
      <v-icon icon="mdi-party-popper"></v-icon>
    </h1>
    <Images />
  </div>
</template>

<script>
import Confetti from "./Confetti.vue";
import Images from "./Images.vue";
export default {
  components: {
    Confetti,
    Images,
  },
  data: () => {
    return {
      click: true,
      animation: false,
      main: true,
    };
  },
  methods: {
    clicked() {
      this.click = false;
      this.animation = true;
      setInterval(() => {
        this.animation = false;
        this.main = true;
      }, 1000);
    },
  },
};
</script>

<style>
.center {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.title {
  font-size: 50px;
  animation: bounce 1s infinite;
  bottom: 0;
  position: absolute;
  left: 50%;
  top: 40%;
  transform: translate(-50%, -50%);
}

@keyframes bounce {
  0% {
    bottom: 5px;
  }
  25%,
  75% {
    bottom: 15px;
  }
  50% {
    bottom: 20px;
  }
  100% {
    bottom: 0;
  }
}

.main {
  background-color: #654ea3;
  width: 100%;
  height: 100%;
  color: #fff;
}

.heart {
  background-color: #654ea3;
  width: 50px;
  height: 50px;
  position: relative;
  transform: rotate(45deg);
  margin-left: 30px;
  animation: zoomInHeart 1s;
}

.heart::before,
.heart::after {
  position: absolute;
  content: "";
  width: 50px;
  height: 50px;
  background-color: #654ea3;
  border-radius: 50%;
}

.heart::before {
  left: -25px;
}

.heart::after {
  top: -25px;
}

@keyframes zoomInHeart {
  from {
    transform: scale(0);
  }
  to {
    transform: scale(40);
  }
}
</style>
