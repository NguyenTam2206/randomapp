<template>
  <section id="pricing" class="pb-8">
    <v-container fluid>
      <v-row align="center" justify="center">
        <v-col cols="10">
          <v-card style="width: 100%">
            <h1
              class="text-center pt-6 font-weight-light"
              :style="$device.isDesktop ? 'font-size : 45px;': 'font-size : 25px;'"
            >Đánh giá từ khách hàng</h1>
            <v-divider class="my-6"></v-divider>
            <div class="text-center">
              <swiper class="swiper" :options="swiperOption">
                <swiper-slide v-for="(item,i) in testimonial" :key="i">
                  <div class="flex-center px-4">
                    <v-card-text>
                      <div class="flex-center">
                        <div class="circle1">
                          <div class="circle2">
                            <v-icon
                              color="#175A83"
                              size="100"
                            >{{item.gender === 1 ? 'mdi-face-man' : 'mdi-face-woman'}}</v-icon>
                          </div>
                        </div>
                      </div>
                      <div class="text--disabled text-uppercase text-h5 my-2">{{item.name}}</div>
                      <v-divider class="my-2" />
                      <div class="text-uppercase">{{item.mess}}</div>
                      <v-rating
                        v-model="item.rating"
                        background-color="indigo lighten-3"
                        color="#175A83"
                        large
                      ></v-rating>
                    </v-card-text>
                    <v-divider style="margin-right: -23px" class="devider" vertical></v-divider>
                  </div>
                </swiper-slide>
              </swiper>
            </div>

            <!-- <v-col class="col-12 col-sm-6 col-md-4" v-for="(item,i) in testimonial" :key="i">
                <div class="flex-center">
                  <v-card-text>
                    <div class="flex-center">
                      <div class="circle1">
                        <div class="circle2">
                          <v-icon
                            color="#175A83"
                            size="100"
                          >{{item.gender === 1 ? 'mdi-face-man' : 'mdi-face-woman'}}</v-icon>
                        </div>
                      </div>
                    </div>
                    <div class="text--disabled text-uppercase text-h5 my-2">{{item.name}}</div>
                    <v-divider class="my-2" />
                    <div class="text-uppercase">{{item.mess}}</div>
                    <v-rating
                      v-model="item.rating"
                      background-color="indigo lighten-3"
                      color="#175A83"
                      large
                    ></v-rating>
                  </v-card-text>
                  <v-divider style="margin-right: -23px" vertical></v-divider>
                </div>
            </v-col>-->
          </v-card>
        </v-col>
      </v-row>
    </v-container>
    <div class="svg-border-rounded text-light">
      <!-- <svg
        xmlns="http://www.w3.org/2000/svg"
        viewBox="0 0 144.54 17.34"
        preserveAspectRatio="none"
        fill="currentColor"
      >
        <path
          d="M144.54,17.34H0V0H144.54ZM0,0S32.36,17.34,72.27,17.34,144.54,0,144.54,0"
        />
      </svg>-->
      <svg
        xmlns="http://www.w3.org/2000/svg"
        viewBox="0 0 1440 320"
        preserveAspectRatio="none"
        fill="currentColor"
      >
        <path
          d="M0,64L80,90.7C160,117,320,171,480,181.3C640,192,800,160,960,138.7C1120,117,1280,107,1360,101.3L1440,96L1440,320L1360,320C1280,320,1120,320,960,320C800,320,640,320,480,320C320,320,160,320,80,320L0,320Z"
        />
      </svg>
    </div>
  </section>
</template>
<style lang="scss">
$main_color: #283e79;

ul {
  font-size: 13px;
  line-height: 1.5em;
  margin: 5px 0 15px;
  padding: 0;

  li {
    list-style: none;
    position: relative;
    padding: 0 0 0 20px;
  }

  li {
    &::before {
      content: "";
      position: absolute;
      left: 0;
      top: 5px;
      width: 10px;
      height: 10px;
      background-color: $main_color;
      border-radius: 50%;
      -moz-border-radius: 50%;
      -webkit-eeborder-radius: 50%;
    }
  }
}
</style>

<style scoped>
.header {
  background-color: #283e79;
  color: white;
}

.circle1 {
  border-radius: 50%;
  width: 150px;
  height: 150px;
  background-color: #f0f8ff;
  display: flex;
  align-items: center;
  justify-content: center;
}

.circle2 {
  border-radius: 50%;
  width: 100px;
  height: 100px;
  background-color: #e0effc;
  display: flex;
  align-items: center;
  justify-content: center;
}

.flex-center {
  display: flex;
  align-items: center;
  justify-content: center;
}

.svg-border-rounded svg {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  color: #f4f7f5;
  z-index: -1;
}

#pricing {
  z-index: 0;
}

.content {
  z-index: 1;
}

svg {
  overflow: hidden;
}

section {
  position: relative;
}
</style>

<script>
import { testimonial } from "@/static/datajson.js";
import { Swiper, SwiperSlide, directive } from "vue-awesome-swiper";
import "swiper/css/swiper.css";
export default {
  components: {
    Swiper,
    SwiperSlide
  },
  directives: {
    swiper: directive
  },
  data: () => ({
    testimonial,
    swiperOption: {
      autoplay: {
        delay: 3000,
        disableOnInteraction: false
      },
      breakpoints: {
        1024: {
          slidesPerView: 3,
          spaceBetween: 0
        },
        768: {
          slidesPerView: 2,
          spaceBetween: 0
        },
        640: {
          slidesPerView: 2,
          spaceBetween: 0
        },
        320: {
          slidesPerView: 1,
          spaceBetween: 0
        }
      }
    }
  }),
  computed: {
    size() {
      const size = { md: "large", xl: "x-large" }[
        this.$vuetify.breakpoint.name
      ];
      return size ? { [size]: true } : {};
    }
  }
};
</script>