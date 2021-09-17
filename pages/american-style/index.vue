<template>
  <div>
    <canvas id="hero-lightpass" />
    <div style='height: 100vh; color: red; border: 1px solid red'>
      qsdfqsdfqsdfqsdf
    </div>
  </div>
</template>

<script>
export default {
  // mounted() {
  //   this.scrollAnimation();
  // },
  // methods: {
  //   scrollAnimation() {
  //     const canvas =  document.getElementById("hero-lightpass");
  //     const context = canvas.getContext("2d");

  //     canvas.width = 1158;
  //     canvas.height = 770;

  //     const frameCount = 147;
  //     const currentFrame = index => (
  //       `https://www.apple.com/105/media/us/airpods-pro/2019/1299e2f5_9206_4470_b28e_08307a42f19b/anim/sequence/large/01-hero-lightpass/${(index + 1).toString().padStart(4, '0')}.jpg`
  //     );

  //     const images = []
  //     const airpods = {
  //       frame: 0
  //     };

  //     for (let i = 0; i < frameCount; i++) {
  //       const img = new Image();
  //       img.src = currentFrame(i);
  //       images.push(img);
  //     }

  //     this.$gsap.to(airpods, {
  //       frame: frameCount - 1,
  //       snap: "frame",
  //       scrollTrigger: {
  //         scrub: 0.5,
  //         markers: true,
  //         scrub: true,
  //       },
  //       onUpdate: render // use animation onUpdate instead of scrollTrigger's onUpdate
  //     });

  //     images[0].onload = render;

  //     function render() {
  //       context.clearRect(0, 0, canvas.width, canvas.height);
  //       context.drawImage(images[airpods.frame], 0, 0);
  //     }
  //   }
  // }
}
</script>

<style>
html {
  height: 100vh;
}

body {
  height: 5000px;
  background: #000;
}

canvas {
  position: fixed;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  max-width: 100vw;
  max-height: 100vh;
}
</style>