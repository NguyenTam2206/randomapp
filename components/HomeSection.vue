<template>
  <section id="hero">
    <v-parallax dark :src="require('@/assets/img/bgHero.jpg')" height="750">
      <v-row align="center" justify="center">
        <v-col cols="12">
          <v-row align="center" justify="center">
            <v-col cols="12" md="5" xl="8" class="wrap-random">
              <h1 class="font-weight-bold mb-4 title-random">Quay số ngẫu nhiên</h1>
              <v-text-field v-model="minNumber" label="Nhập số nhỏ nhất" solo type="number"></v-text-field>
              <v-text-field v-model="maxNumber" label="Nhập số lớn nhất" solo type="number"></v-text-field>
              <div>
                <v-btn outlined block large dark @click="randomIntFromInterval">
                  Quay Ngay
                  <v-icon class="ml-2">mdi-arrow-down</v-icon>
                </v-btn>
              </div>

              <div v-if="result" class="mt-8" id="realresult">
                <div>{{result}}</div>
              </div>
              <div v-show="showfake" class="mt-8" id="fakeresult"></div>
            </v-col>
            <v-col cols="12" md="7" xl="4" class="hidden-sm-and-down"></v-col>
          </v-row>
        </v-col>
      </v-row>
      <div class="svg-border-waves text-white">
        <v-img :src="require('@/assets/img/borderWaves.svg')" />
      </div>
    </v-parallax>
    <v-container fluid id="features" class="mt-2">
      <v-row align="center" justify="center">
        <v-col cols="10">
          <v-row align="center" justify="space-around">
            <!-- <v-col cols="12" class="text-center">
              <h1 class="font-weight-light display-2">Title</h1>
              <h1 class="font-weight-light">
                Lorem ipsum dolor sit amet consectetur adipisicing elit.
              </h1>
            </v-col>-->
            <v-col cols="12" sm="4" class="text-center" v-for="(feature, i) in features" :key="i">
              <v-hover v-slot:default="{ hover }">
                <v-card class="card" shaped :elevation="hover ? 10 : 4" :class="{ up: hover }">
                  <v-img
                    :src="feature.img"
                    max-width="100px"
                    class="d-block ml-auto mr-auto"
                    :class="{ 'zoom-efect': hover }"
                  ></v-img>
                  <h1 class="font-weight-regular">{{ feature.title }}</h1>
                  <h4 class="font-weight-regular" style="font-size : 20px;">{{ feature.text }}</h4>
                </v-card>
              </v-hover>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </v-container>
    <div class="svg-border-waves">
      <img src="~@/assets/img/wave2.svg" />
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      dialog: false,
      videoId: "i8IvvHJssWE",
      features: [
        {
          img: require("@/assets/img/icon2.png"),
          title: "Hàng đầu",
          text: "Là đối tác 1000+ sự kiện quay số online đã được tổ chức."
        },
        {
          img: require("@/assets/img/icon1.png"),
          title: "Bảo mật",
          text:
            "Thuật toán không thể can thiệp kết quả. Hoàn toàn là ngẫu nhiên."
        },
        {
          img: require("@/assets/img/icon3.png"),
          title: "Uy tín",
          text:
            "Hàng ngàn cửa hàng, fanpage tin dùng. Quay số ngẫu nhiên công bằng tuyệt đối."
        }
      ],
      minNumber: 1,
      maxNumber: 100,
      result: "",
      fakeresult: "",
      showfake: false
    };
  },
  watch: {
    minNumber(val, oldVal) {
      if (Number(val) > Number(this.maxNumber)) {
        this.maxNumber = Number(val) + 10;
      }
    }
  },
  methods: {
    randomIntFromInterval() {
      this.result = "";
      if (Number(this.maxNumber) < Number(this.minNumber)) {
        let maxNumber = Number(this.maxNumber);
        let minNumber = Number(this.minNumber);
        this.maxNumber = minNumber;
        this.minNumber = maxNumber;
      }
      setInterval;
      let result = Math.floor(
        Math.random() * (Number(this.maxNumber) - Number(this.minNumber) + 1) +
          Number(this.minNumber)
      );
      this.effectNumber(result);
    },
    effectNumber(result) {
      this.showfake = true;
      let ele = document.getElementById("fakeresult");
      // Animate!
      let effect = setInterval(function() {
        ele.innerHTML =
          Math.floor(Math.random() * 100) + Math.floor(Math.random() * 100);
      }, 50);
      setTimeout(() => {
        clearInterval(effect);
        this.showfake = false;
        this.result = result;
      }, 1000);
    }
  }
};
</script>

<style lang="scss">
#fakeresult {
  background: #ffffff;
  height: 48px;
  width: 100%;
  border-radius: 4px;
  text-align: center;
  color: black;
  font-weight: bold;
  font-size: 16px;
  padding-top: 12px;
}
#realresult {
  background: #ffffff;
  height: 48px;
  width: 100%;
  border-radius: 4px;
  text-align: center;
  color: black;
  font-weight: bold;
  font-size: 16px;
  padding-top: 12px;
}
.circle {
  stroke: white;
  stroke-dasharray: 650;
  stroke-dashoffset: 650;
  -webkit-transition: all 0.5s ease-in-out;
  opacity: 0.3;
}

.playBut {
  /*  border: 1px solid red;*/
  display: inline-block;
  -webkit-transition: all 0.5s ease;

  .triangle {
    -webkit-transition: all 0.7s ease-in-out;
    stroke-dasharray: 240;
    stroke-dashoffset: 480;
    stroke: white;
    transform: translateY(0);
  }

  &:hover {
    .triangle {
      stroke-dashoffset: 0;
      opacity: 1;
      stroke: white;
      animation: nudge 0.7s ease-in-out;

      @keyframes nudge {
        0% {
          transform: translateX(0);
        }
        30% {
          transform: translateX(-5px);
        }
        50% {
          transform: translateX(5px);
        }
        70% {
          transform: translateX(-2px);
        }
        100% {
          transform: translateX(0);
        }
      }
    }

    .circle {
      stroke-dashoffset: 0;
      opacity: 1;
    }
  }
}
</style>

<style>
.btn-play {
  transition: 0.2s;
}

.svg-border-waves .v-image {
  position: absolute;
  bottom: 0;
  left: 0;
  height: 3rem;
  width: 100%;
  overflow: hidden;
}

#hero {
  z-index: 0;
}
.svg-border-waves img {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  margin-bottom: -2px;
  z-index: -1;
}

.card {
  min-height: 300px;
  padding: 10px;
  transition: 0.5s ease-out;
}

.card .v-image {
  margin-bottom: 15px;
  transition: 0.75s;
}

.card h1 {
  margin-bottom: 10px;
}

.zoom-efect {
  transform: scale(1.1);
}

.up {
  transform: translateY(-20px);
  transition: 0.5s ease-out;
}
.title-random {
  font-size: 3rem;
}
.result input {
  text-align: center !important;
}
@media (min-width: 769px) {
  .wrap-random {
    padding-left: 100px !important;
  }
}
@media (max-width: 768px) {
  .title-random {
    font-size: 2rem;
  }
  .wrap-random {
    padding-left: 12px !important;
  }
  .devider {
    display: none;
  }
}
</style>

<style>
section {
  position: relative;
}
</style>
