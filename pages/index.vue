<template>
  <div class="main_container">
    <div class="images_container">
      <img id="logo_img" v-on:click="blinkLogo" src="pr3sto_logo.png" />
      <img id="letter_img" src="pr3sto_logo_p.png" />
    </div>
  </div>
</template>

<style>
.main_container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-content: center;
  align-items: center;
  background: #000;
}

.images_container {
  position: relative;
  width: 500px;
  height: 500px;
}

.images_container > img {
  position: absolute;
  width: 500px;
  top: 0;
  left: 0;
}

#letter_img {
  pointer-events: none;
  display: none;
}
</style>

<script>
export default {
  data() {
    return {
      animationRequestId: 0,
      letterCounter: 0,
      letterIndexes: ["p", "r", "3", "s", "t", "o"]
    };
  },
  methods: {
    blinkLogo: function() {
      if (this.animationRequestId != 0) {
        cancelAnimationFrame(this.animationRequestId);
      }

      var letterImg = document.getElementById("letter_img");
      var logoImg = document.getElementById("logo_img");

      // change letter image
      letterImg.src = "pr3sto_logo_" + this.letterIndexes[this.letterCounter] + ".png";

      logoImg.style.opacity = 0.65;
      letterImg.style.opacity = 1;
      letterImg.style.display = "block";

      // blink letter and logo
      const blink = () => {
        logoImg.style.opacity = parseFloat(logoImg.style.opacity) + 0.01;
        letterImg.style.opacity = parseFloat(letterImg.style.opacity) - 0.02;

        if (logoImg.style.opacity == 1) {
          letterImg.style.display = "none";
        } else {
          this.animationRequestId = requestAnimationFrame(blink);
        }
      };
      blink();

      if ((this.letterCounter += 1) == 6) {
        this.letterCounter = 0;
      }
    }
  }
};
</script>
