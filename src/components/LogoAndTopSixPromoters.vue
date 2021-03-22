<template>
  <div class="logo-top-promoters-container">
    <img
      class="logo-rounded-circle"
      alt="100x100"
      src="https://www.pikpng.com/pngl/b/583-5830237_your-logo-retulp-bus-stop-clipart.png"
      data-holder-rendered="true"
    />
    <div class="avatars">
      <div class="avatar" v-for="img in imgs" :key="img">
        <div ref="thumb" class="thumb">
          <img @mouseenter="enlargeImg" @mouseleave="reduceImg" :src="img" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      classes: ["one", "two", "three", "four", "five", "six"],
      degs: [0, -60, -120, 180, 120, 60],
      imgs: [
        "https://static.toiimg.com/photo/72975551.cms",
        "https://cdn.pixabay.com/photo/2015/04/23/22/00/tree-736885__340.jpg",
        "https://webmeup.com/upload/blog/lead-image-105.png",
        "https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcRFU7U2h0umyF0P6E_yhTX45sGgPEQAbGaJ4g&usqp=CAU",
        "https://pin.dekhnews.com/wp-content/uploads/2019/09/lord-shiva-images-1.jpg",
        "https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcSy1uZTBlxjOfVEiZsIt9FSo_bkxgEb6_OslQ&usqp=CAU",
      ],
    };
  },

  mounted() {
    console.clear();
    this.$refs.thumb.forEach((el, index) => {
      el.classList.add(`${this.classes[index]}`);
      el.parentElement.setAttribute(
        "style",
        "transform: rotate(" + this.degs[index] + "deg) translateY(-150px);"
      );
    });
  },
  methods: {
    enlargeImg: function (event) {
      event.target.setAttribute("style", "transform: scale(1.4);");
    },
    reduceImg: function (event) {
      event.target.setAttribute("style", "transform: scale(1);");
    },
  },
};
</script>

<style scoped>
.logo-top-promoters-container {
  background-color: rgb(34, 33, 33);
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  user-select: none;
}
.logo-rounded-circle {
  position: absolute;
  height: 160px;
  width: 160px;
  left: calc(50% - 80px);
  top: calc(50% - 80px);
  border-radius: 50%;
  background: grey;
}

/* rotate all elements 360deg */
.avatars {
  position: absolute;
  top: 50%;
  left: 50%;
  animation: spinAvatars 30s linear infinite;
}
@keyframes spinAvatars {
  100% {
    transform: rotate(360deg);
  }
}

/* .thumb img containers */
.avatar {
  position: absolute;
  left: calc(50% - 50px);
  top: calc(50% - 50px);
}
.thumb {
  width: 100px;
  height: 100px;
}
/* turning thumbs backwards to appear straight always */
.one {
  animation: backward 30s linear infinite;
}
@keyframes backward {
  100% {
    transform: rotate(-360deg);
  }
}
.two {
  transform: rotate(60deg);
  animation: backward2 30s linear infinite;
}
@keyframes backward2 {
  100% {
    transform: rotate(-300deg);
  }
}
.three {
  transform: rotate(120deg);
  animation: backward3 30s linear infinite;
}
@keyframes backward3 {
  100% {
    transform: rotate(-240deg);
  }
}
.four {
  transform: rotate(180deg);
  animation: backward4 30s linear infinite;
}
@keyframes backward4 {
  100% {
    transform: rotate(-180deg);
  }
}
.five {
  transform: rotate(240deg);
  animation: backward5 30s linear infinite;
}
@keyframes backward5 {
  100% {
    transform: rotate(-120deg);
  }
}
.six {
  transform: rotate(300deg);
  animation: backward6 30s linear infinite;
}
@keyframes backward6 {
  100% {
    transform: rotate(-60deg);
  }
}

/* process images to fit without loosing ratio and animate zoom in/out*/
.thumb img {
  width: 100px;
  height: 100px;
  transition: 0.5s cubic-bezier(0.4, 0, 0.2, 1);
  border-radius: 50%;
  object-fit: cover;
  box-shadow: 0 0 0 4px white;
}
</style>