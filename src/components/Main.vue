<template>
  <div class="main">
    <div class="center" v-if="click">
    <h1>Clique em mim</h1>
      <v-btn variant="plain"
             style="background-color: transparent; box-shadow: none; color: transparent;"
             @click="clicked">
        <img src="../assets/images/bolinha.png" />
      </v-btn>
    </div>

    <div v-else>
      <v-container class="falling-balls" fluid>
        <div
          v-for="n in balls"
          :key="n.id"
          class="ball"
          :style="{
            left: n.left + '%',
            animationDuration: n.duration + 's',
            animationDelay: n.delay + 's'
          }"
        >
          <img
            src="../assets/images/bolinha.png"
            alt="bolinha"
            class="ball-image"
          />
        </div>

        <v-container class="data-container">
          <v-avatar size="200" class="bolinha" color="#d9851e">
            <span class="data">13/06</span>
          </v-avatar>
        </v-container>

        <div class="center">
          <h1 class="alfa-slab-one-regular">BEACH TENNIS</h1>
          <h1 class="alfa-slab-one-regular">DA JÚLINHA</h1>
        </div>

        <div class="info">
          <h1>Local: ALOB</h1>
          <h1>Horário: 19:30h</h1>
        </div>

        <div class="traje">
          <h1>Traje Esportivo</h1>
        </div>

        <div class="center d-flex">
          <img src="../assets/images/raquete.png" />
          <h1 class="convite-texto">Aguardamos sua presença</h1>
          <img src="../assets/images/raquete.png" style="transform: scale(-1, 1);" />
        </div>
      </v-container>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const balls = ref(
  Array.from({ length: 30 }, (_, i) => ({
    id: i,
    left: Math.random() * 100,
    duration: 3 + Math.random() * 3,
    delay: Math.random() * 5
  }))
)
</script>

<script>
export default {
  data() {
    return {
      click: true,
    }
  },
  methods: {
    clicked() {
      this.click = false
    },
  }
}
</script>

<style>
body, html, #app {
  margin: 0;
  padding: 0;
  height: 100%;
}

.main {
  background-color: #809ae0;
  width: 100%;
  height: 100%;
  color: #fff;
  overflow-x: hidden;
}

img {
  max-width: 100%;
  height: auto;
}

h1 {
  font-size: clamp(24px, 5vw, 70px);
  margin: 0;
}


.falling-balls {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  overflow: hidden;
  pointer-events: none;
  z-index: 9999;
}

.ball {
  position: absolute;
  top: -20px;
  width: 36px;
  height: 36px;
  border-radius: 50%;
  opacity: 0.8;
  animation-name: fall;
  animation-timing-function: linear;
  animation-iteration-count: infinite;
}

.ball-image {
  width: 100%;
  height: 100%;
  object-fit: contain;
}

@keyframes fall {
  to {
    transform: translateY(110vh);
  }
}

.center {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.center.d-flex {
  flex-direction: row;
  flex-wrap: wrap;
  gap: 20px;
}

.center.d-flex img {
  height: clamp(150px, 20vw, 350px);
}

.convite-texto {
  width: clamp(200px, 60vw, 400px);
  padding-top: 50px;
}


.info, .traje {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  gap: 20px;
  margin-top: 20px;
}

.info h1, .traje h1 {
  font-size: clamp(20px, 4vw, 40px);
}

.data-container {
  position: fixed;
  top: -15px;
  left: 68%;
  z-index: 1000;
}

.v-avatar {
  width: clamp(120px, 20vw, 200px) !important;
  height: clamp(120px, 20vw, 200px) !important;
}

.data {
  font-size: clamp(30px, 5vw, 60px);
}

.alfa-slab-one-regular {
  font-family: "Alfa Slab One", serif;
  font-weight: 400;
  font-style: normal;
}

.bolinha {
  animation: piscar 1s infinite;
}

@keyframes piscar {
  0%, 100% {
    opacity: 1;
  }
  50% {
    opacity: 0;
  }
}
</style>
