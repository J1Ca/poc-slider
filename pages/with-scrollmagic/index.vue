<template>
  <div>
    <div class="hero">
      <h2 class="reverseText">dsqdqsdqsdqs</h2>
      <canvas id="hero-lightpass"/>
    </div>
    <div class="box">
      <h2 class="text1" style="color: white">Scroll trigger</h2>
      <h2 class="text2" style="color: white">This is my first one</h2>
      <h2 class="text3" style="color: red">How is it?</h2>
    </div>

    <div class="box2">
      <h2 class="text4">Let get out</h2>
      <h2 class="text5">of this town</h2>
      <h2 class="text6">Drive out the city</h2>
    </div>
  </div>
</template>

<script>
export default {
  mounted() {
    this.scrollAnimation();
  },
  methods: {
    scrollAnimation() {
      const canvas = document.getElementById("hero-lightpass");
      const context = canvas.getContext("2d");

      canvas.width = 1158;
      canvas.height = 770;

      const frameCount = 147;
      const currentFrame = index => (
        `https://www.apple.com/105/media/us/airpods-pro/2019/1299e2f5_9206_4470_b28e_08307a42f19b/anim/sequence/large/01-hero-lightpass/${(index + 1).toString().padStart(4, '0')}.jpg`
      );

      const images = []
      const airpods = {
        frame: 0
      };

      for (let i = 0; i < frameCount; i++) {
        const img = new Image();
        img.src = currentFrame(i);
        images.push(img);
      }

      const airPodsAnimation = this.$gsap.to(airpods, {
        frame: frameCount - 1,
        snap: "frame",
        onUpdate:render
      });

      this.$ScrollTrigger.create({
        animation: airPodsAnimation,
        trigger: ".reverseText",
        start: "-=100",
        endTrigger: '#hero-lightpass',
        end: "bottom top",
        scrub: 0.5,
        // markers: true,
      });

      render();
      function render() {
        context.clearRect(0, 0, canvas.width, canvas.height);
        context.drawImage(images[airpods.frame], 0, 0);
      }


      this.$gsap.timeline({
        scrollTrigger: {
          id: 'hero-test',
          trigger: ".reverseText",
          start: "-=100",
          end: "+=50",
          // markers: true,
          scrub: true,
          //onUpdate: () => console.log('startttt'),
        }
      })
      .to(".reverseText", {y: -15, opacity: 0, duration: 1})

      const test = this.$gsap.timeline()
      .from(".text1", { x : innerWidth * 1, opacity: 0 })
      .from(".text2", { x : innerWidth * 1, opacity: 0 })

      this.$ScrollTrigger.create({
        animation: test,
        trigger: "#hero-lightpass",
        start: "center center",
        end: "bottom top",
        scrub: true,
        pin: true,
        pinSpacing: false,
      })

      this.$gsap.timeline({
        scrollTrigger: {
          trigger: ".box2",
          start: "center center",
          end: "bottom top",
          scrub: true,
          pin: true,
        }
      })
      .from(".text4", { x : innerWidth * 1, opacity: 0 })
      .from(".text5", { x : innerWidth * 1, opacity: 0 })
    },
  }
};
</script>

<style>
h2 {
  margin-top: 200px;
  margin-bottom: 200px;
}
.hero {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  height: fit-content;
}
</style>
