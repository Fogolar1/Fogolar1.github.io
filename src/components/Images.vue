<template>
  <div class="images">
    <img src="../assets/love/4.png" class="image-item" />
    <img src="../assets/love/5.jpeg" class="image-item" />
    <img src="../assets/love/9.jpeg" class="image-item" />
    <img src="../assets/love/11.jpeg" class="image-item" />
    <img src="../assets/love/12.jpeg" class="image-item" />
    <img src="../assets/love/13.jpeg" class="image-item" />
    <img src="../assets/love/14.jpeg" class="image-item" />
    <img src="../assets/love/15.jpeg" class="image-item" />
    <img src="../assets/love/17.jpeg" class="image-item" />
    <img src="../assets/love/21.jpeg" class="image-item" />
    <img src="../assets/love/23.jpeg" class="image-item" />
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
img {
  height: 300px;
  width: 300px;
  aspect-ratio: 3/2;
  object-fit: contain;
  position: absolute;
  top: 25%;
  opacity: 0;
  animation: appear 10s infinite;
}

.image-item:nth-child(1) {
  left: 38%;
  top: 55%;
  animation-delay: 0.5s;
}

.image-item:nth-child(2) {
  left: 59%;
  top: 57%;
  animation-delay: 1.5s;
}

.image-item:nth-child(3) {
  left: 20%;
  top: 30%;
  animation-delay: 1.7s;
}

.image-item:nth-child(4) {
  left: 40%;
  top: 22%;
  animation-delay: 2.4s;
}

.image-item:nth-child(5) {
  left: 60%;
  animation-delay: 3.2s;
}

.image-item:nth-child(6) {
  left: 80%;
  top: 30%;
  animation-delay: 4.7s;
}

.image-item:nth-child(7) {
  left: 29%;
  top: 36%;
  animation-delay: 6.1s;
}

.image-item:nth-child(8) {
  left: 70%;
  top: 40%;
  animation-delay: 7s;
}

.image-item:nth-child(9) {
  left: 50%;
  top: 30%;
  animation-delay: 9.5s;
}

.image-item:nth-child(10) {
  left: 10%;
  top: 40%;
  animation-delay: 11.5s;
}

.image-item:nth-child(11) {
  left: 84%;
  top: 60%;
  animation-delay: 12.5s;
}
@keyframes appear {
  from {
    opacity: 0;
  }
  50% {
    opacity: 1;
  }
  to {
    opacity: 0;
  }
}
</style>
