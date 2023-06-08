<script>
import { VueperSlides, VueperSlide } from "vueperslides";
import "vueperslides/dist/vueperslides.css";
import patternOne from "@/assets/pattern-art-one.jpg";
import patternTwo from "@/assets/pattern-art-two.jpg";
import patternThree from "@/assets/pattern-art-three.jpg";

export default {
  components: {
    VueperSlides,
    VueperSlide,
  },
  data: () => ({
    slides: [
      {
        title: "Slide #1",
        content: "Slide 2 content.",
        image: patternOne,
      },
      {
        title: "Slide #2",
        content: "Slide 2 content.",
        image: patternTwo,
      },
      {
        title: "Slide #3",
        content: "Slide 2 content.",
        image: patternThree,
      },
    ],
  }),
};
</script>

<template>
  <div class="slider">
    <vueper-slides>
      <vueper-slide v-for="(slide, i) in slides" :key="i" :image="slide.image">
      </vueper-slide>
    </vueper-slides>
  </div>

  <div class="header-container">
    <div>
      <h1 class="title">WELCOME</h1>
    </div>
    <div class="intro-text">
      <p>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur
        pulvinar semper enim non cursus. In pellentesque volutpat sapien, ac
        scelerisque nisl laoreet vitae. Nunc felis justo, dapibus ac ultrices
        sed, blandit vel erat. Aliquam tincidunt varius nulla dignissim
        vulputate. Nulla est nibh, mattis eget nisi vel, placerat venenatis
        lorem. Praesent id rutrum erat. Quisque pharetra tristique enim eu
        congue. Cras in dolor in mi posuere vehicula ac sed quam. Pellentesque
        sed enim et leo accumsan interdum. Proin pretium sit amet ante nec
        dignissim. Phasellus feugiat, mauris et congue elementum, sapien ipsum
        tempus justo, nec tempus urna dolor ut mauris. Donec egestas fringilla
        ipsum consectetur pretium.
      </p>
      <p>
        Donec et ante eu risus lobortis malesuada nec ut dui. Morbi ac odio
        lobortis enim feugiat maximus vel vel ante. Aenean tincidunt mattis ex
        lobortis sollicitudin. Nullam quis volutpat augue, non pellentesque
        libero. Quisque nec dictum urna. Maecenas ullamcorper pretium nibh eget
        facilisis. Sed volutpat mattis blandit. Ut hendrerit in enim ut
        malesuada. Suspendisse gravida ligula tortor, id finibus nibh accumsan
        at. Suspendisse fermentum ultrices tristique. Donec id nibh et augue
        iaculis elementum vitae sed felis. Donec vitae dui vel leo pulvinar
        pellentesque vel id elit. Ut ex nunc, tristique a ornare sed, efficitur
        ac quam. Aliquam rutrum rhoncus auctor.
      </p>
      <p>
        Donec et ante eu risus lobortis malesuada nec ut dui. Morbi ac odio
        lobortis enim feugiat maximus vel vel ante. Aenean tincidunt mattis ex
        lobortis sollicitudin. Nullam quis volutpat augue, non pellentesque
        libero. Quisque nec dictum urna. Maecenas ullamcorper pretium nibh eget
        facilisis. Sed volutpat mattis blandit. Ut hendrerit in enim ut
        malesuada. Suspendisse gravida ligula tortor, id finibus nibh accumsan
        at. Suspendisse fermentum ultrices tristique. Donec id nibh et augue
        iaculis elementum vitae sed felis. Donec vitae dui vel leo pulvinar
        pellentesque vel id elit. Ut ex nunc, tristique a ornare sed, efficitur
        ac quam. Aliquam rutrum rhoncus auctor.
      </p>
    </div>
  </div>
</template>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  border: 0;
}

.header-container {
  margin: 50px 250px 50px 250px;
  align-items: center;
  text-align: center;

  .title {
    text-align: left;
    margin-bottom: 20px;
  }
}

.slider {
  margin-top: 80px;
  width: 100%;
  height: 100%;
  overflow: hidden;
}

.intro-text {
  p {
    font-size: 16px;
    color: rgb(67, 67, 67);
    text-align: justify;
    text-justify: inter-word;
    margin-bottom: 20px;
  }
}

@media only screen and (max-width: 600px) {
  .slider {
    float: none;
    display: block;
    margin-top: 45px;
  }

  .header-container {
    margin: 5px 50px 5px 50px;
    align-items: center;
    text-align: center;

    .title {
      text-align: left;
      margin: 12px;
    }
  }
}
</style>
