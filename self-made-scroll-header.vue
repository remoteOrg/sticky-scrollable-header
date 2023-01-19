<template>
  <main>
    <header :class="{ hide: isHidden }">I am a header</header>
    <section></section>
    <footer></footer>
  </main>
</template>

<script>
export default {
  data() {
    return {
      isHidden: false,
      temp: 0,
      scrollY: 0,
    };
  },
  mounted() {
    window.addEventListener("scroll", this.scrollHeader);
  },
  methods: {
    scrollHeader() {
      this.scrollY = window.scrollY;
      if (this.scrollY == 0) {
        this.isHidden = false;
      }
      if (this.scrollY > this.temp) {
        // scrolled down
        this.isHidden = true;
      } else if (this.scrollY < this.temp) {
        // scrolled up
        this.isHidden = false;
      }
      this.temp = this.scrollY;
    },
  },
};
</script>

<style scoped>
header {
  width: 100%;
  height: 20vh;
  background-color: tomato;
  transform: translateY(0);
  position: fixed;
  transition: transform 0.3s ease;
}
.hide {
  transform: translateY(-20vh);
}
section {
  min-height: 200vh;
  height: 100%;
  width: 100%;
}
</style>
