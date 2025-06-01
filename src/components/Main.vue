<template>
  <div class="main">
    <div class="center" v-if="click">
      <v-btn variant="plain" style="background-color: transparent; box-shadow: none; color: transparent;" @click="this.clicked()">
          <img src="../assets/images/kit_60_bolinhas_de_beach_tennis_jaya_107_3_750a80870191258723a32803661da44d-removebg-preview.png" />
        </v-btn
      >
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
            animationDelay: n.delay + 's',
            backgroundColor: n.color,
          }"
        >
            <img
            src="../assets/images/kit_60_bolinhas_de_beach_tennis_jaya_107_3_750a80870191258723a32803661da44d-removebg-preview.png"
            alt="bolinha"
            class="ball-image"
          />
        </div>

        <v-container style="height: 100vh; padding-left: 70%;">
          <v-avatar
            size="200"
            class="bolinha"
            color="#d9851e"
          >
          <span style="font-size: 60px;">13/06</span>
        </v-avatar>
        </v-container>

        <div class="center">
          <h1 style="font-size: 70px;" class="alfa-slab-one-regular">BEACH TENNIS</h1>
          <h1 style="font-size: 70px; padding-left: 30px;" class="alfa-slab-one-regular">DA JÚLINHA</h1>
        </div>
        <div class="info d-flex">
         <h1 style="margin-right: 50px;">Local : ALOB</h1>
         <h1>Horário : 19:30h</h1>
        </div>
        <div class="traje">
          <h1>Traje Esportivo</h1>
        </div>
        <div class="center d-flex" style="top : 80%;">
          <img src="../assets/images/raquete.png" style="height: 350px;">
          <h1 style="padding-top: 120px; width: 400px;">Aguardamos sua presença</h1>
          <img src="../assets/images/raquete.png" style="height: 350px; transform: scale(-1, 1);">
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
    delay: Math.random() * 5, 
  }))
)
</script>

<script>
export default {
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
  top: 30%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.info{
   position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}

.traje{
   position: absolute;
    top: 60%;
    left: 50%;
    transform: translate(-50%, -50%);
}

.falling-balls {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  overflow: hidden;
  pointer-events: none; /* opcional: permite clicar nos elementos atrás */
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

.main {
  background-color: #809ae0;
  width: 100%;
  height: 100%;
  color: #fff;
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
