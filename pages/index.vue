<template>
  <div class="page-container">
    <div class="content-container">
      <div class="images-section">
        <div class="images">
          <div id="logo-glitch" v-on:click="blinkLogo">
            <div class="logo-glitch__img"></div>
            <div class="logo-glitch__img"></div>
            <div class="logo-glitch__img"></div>
            <div class="logo-glitch__img"></div>
          </div>
          <img id="logo-letter" />
        </div>
      </div>
      <div class="info-section">
        <p>
          <span>Alexey Chirukhin</span>
          <br />
          <img src="/images/location_icon.png" />
          <span>Saint Petersburg, RU</span>
          <br />
          <span
            id="software-link"
            data-text="Software Engineer"
            @mouseover="startGlitchEffect"
            @mouseleave="stopGlitchEffect"
          >Software Engineer</span>
        </p>
      </div>
    </div>
  </div>
</template>

<style lang="sass">
@import "@/assets/styles/glitch-text-animation.scss";
</style>

<style>
@import "@/assets/styles/glitch-animation.css";

:root {
  --gap-horizontal: 3px;
  --gap-vertical: 3px;
  --blend-mode-1: none;
  --blend-mode-2: hard-light;
  --blend-mode-3: hard-light;
  --blend-mode-4: hard-light;
  --blend-color-1: transparent;
  --blend-color-2: red;
  --blend-color-3: green;
  --blend-color-4: blue;
}

.page-container {
  height: 100vh;
  padding: 3vw;
}

.content-container {
  display: grid;
  grid-template-columns: 50% 50%;
  grid-template-rows: 100%;
  height: 100%;
  width: 100%;
  background: #aaa;
  border: 2px solid #000;
  box-shadow: 7px 7px #000;
}

.images-section {
  background: #000;
}

.images {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 10vw;
  height: calc(100% - 20vw);
  width: calc(100% - 20vw);
}

#logo-glitch {
  position: relative;
  width: 100%;
  height: 100%;
  cursor: pointer;
}

.logo-glitch__img {
  position: absolute;
  top: calc(-1 * var(--gap-vertical));
  left: calc(-1 * var(--gap-horizontal));
  width: calc(100% + var(--gap-horizontal) * 2);
  height: calc(100% + var(--gap-vertical) * 2);
  transform: translate3d(0, 0, 0);
  background: url(/images/pr3sto_logo.png) no-repeat 50% 0;
  background-size: contain;
  background-position: center center;
  background-color: var(--blend-color-1);
  background-blend-mode: var(--blend-mode-1);
}
.logo-glitch__img:nth-child(2) {
  background-color: var(--blend-color-2);
  background-blend-mode: var(--blend-mode-2);
}
.logo-glitch__img:nth-child(3) {
  background-color: var(--blend-color-3);
  background-blend-mode: var(--blend-mode-3);
}
.logo-glitch__img:nth-child(4) {
  background-color: var(--blend-color-4);
  background-blend-mode: var(--blend-mode-4);
}
.logo-glitch__img:nth-child(n + 2) {
  mask-image: url(/images/pr3sto_logo.png);
  mask-repeat: no-repeat;
  mask-size: contain;
  mask-position: center center;
  opacity: 0;
}

#logo-letter {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  pointer-events: none;
  display: none;
  max-width: calc(100% + var(--gap-horizontal) * 2);
  max-height: calc(100% + var(--gap-vertical) * 2);
  z-index: 100;
}

.info-section {
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  background: #fff;
}

.info-section--1::before {
  content: "";
  position: absolute;
  display: block;
  width: 100%;
  height: 100%;
  opacity: 0.4;
  background-image: url(/images/bkg1.jpg);
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  filter: grayscale(100%);
  filter: gray;
}
.info-section--2::before {
  content: "";
  position: absolute;
  display: block;
  width: 100%;
  height: 100%;
  opacity: 0.4;
  background-image: url(/images/bkg2.jpg);
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  filter: grayscale(100%);
  filter: gray;
}
.info-section--3::before {
  content: "";
  position: absolute;
  display: block;
  width: 100%;
  height: 100%;
  opacity: 0.4;
  background-image: url(/images/bkg3.jpg);
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  filter: grayscale(100%);
  filter: gray;
}

.info-section > p {
  isolation: isolate;
  text-align: right;
  font-size: 3vw;
}

.info-section > p > img {
  height: 1em;
  vertical-align: text-top;
}

.info-section > p > span {
  display: inline-block;
}

.glitch-text {
  position: relative;
  color: white;
  animation: glitch-anim-text-skew 2s infinite linear alternate-reverse;
}

.glitch-text::before {
  content: attr(data-text);
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  left: 1px;
  text-shadow: -1px 0 #ff00c1;
  animation: glitch-anim-text-1 5s infinite linear alternate-reverse;
}

.glitch-text::after {
  content: attr(data-text);
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  left: -1px;
  text-shadow: -1px 0 #00fff9, 1px 1px #ff00c1;
  animation: glitch-anim-text-2 1s infinite linear alternate-reverse;
}

@media screen and (max-width: 600px) {
  .content-container {
    display: grid;
    grid-template-columns: 100%;
    grid-template-rows: 50% 50%;
  }

  .info-section > p {
    font-size: 5vw;
  }
}
</style>

<script>
export default {
  data() {
    return {
      animationRequestId: 0,
      letterIndex: 0,
      letterImages: []
    };
  },
  mounted: function() {
    this.init();
  },
  methods: {
    init: function() {
      var el = document.getElementsByClassName("info-section")[0];
      var n = Math.floor(Math.random() * 3) + 1; // random in [1,2,3]
      el.classList.add("info-section--" + n);

      var p = new Image();
      p.src = "/images/pr3sto_logo_p.png";
      this.letterImages.push(p);
      var r = new Image();
      r.src = "/images/pr3sto_logo_r.png";
      this.letterImages.push(r);
      var _3 = new Image();
      _3.src = "/images/pr3sto_logo_3.png";
      this.letterImages.push(_3);
      var s = new Image();
      s.src = "/images/pr3sto_logo_s.png";
      this.letterImages.push(s);
      var t = new Image();
      t.src = "/images/pr3sto_logo_t.png";
      this.letterImages.push(t);
      var o = new Image();
      o.src = "/images/pr3sto_logo_o.png";
      this.letterImages.push(o);
    },
    blinkLogo: function() {
      if (this.animationRequestId != 0) {
        cancelAnimationFrame(this.animationRequestId);
      }

      var letterImg = document.getElementById("logo-letter");
      var logoImg = document.getElementById("logo-glitch");

      // change letter image
      letterImg.src = this.letterImages[this.letterIndex].src;

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

      this.letterIndex = (this.letterIndex + 1) % 6;
    },
    startGlitchEffect: function() {
      var browserSupport = CSS.supports(`(-webkit-clip-path: polygon(0 0, 0 0, 0 0, 0 0)) or
        (clip-path: polygon(0 0, 0 0, 0 0, 0 0))`);

      // don't apply glitch effect if browser does not support 'clip-path'
      if (!browserSupport) return;

      // apply glitch to text
      var softwareLink = document.getElementById("software-link");
      softwareLink.classList.add("glitch-text");

      // apply glitch to logo
      var images = document.getElementsByClassName("logo-glitch__img");

      images[1].style.opacity = 1;
      images[1].style.transform = "translate3d(var(--gap-horizontal),0,0)";
      images[1].style.animation = "glitch-anim-1 2s infinite linear alternate";

      images[2].style.opacity = 1;
      images[2].style.transform =
        "translate3d(calc(-1 * var(--gap-horizontal)),0,0)";
      images[2].style.animation = "glitch-anim-2 2s infinite linear alternate";

      images[3].style.opacity = 1;
      images[3].style.transform =
        "translate3d(calc(-1 * var(--gap-horizontal)),0,0) rotateY(20deg) rotateZ(1deg)";
      images[3].style.animation = "glitch-anim-3 2s infinite linear alternate";
    },
    stopGlitchEffect: function() {
      // remove glitch from text
      var softwareLink = document.getElementById("software-link");
      softwareLink.classList.remove("glitch-text");

      // remove glitch from logo
      var images = document.getElementsByClassName("logo-glitch__img");
      Array.from(images)
        .slice(1)
        .forEach(element => {
          element.style.opacity = 0;
          element.style.transform = "";
          element.style.animation = "";
        });
    }
  }
};
</script>
