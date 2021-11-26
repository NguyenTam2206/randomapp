<template>
  <section id="download">
    <v-container fluid>
      <v-row align="center" justify="center">
        <v-col cols="10">
          <v-row align="center" justify="center">
            <v-col sm="4" class="hidden-xs-only">
              <v-img
                :src="require('@/assets/img/ill2.svg')"
                class="d-block ml-auto mr-auto"
                max-width="350px"
              />
            </v-col>
            <v-col cols="12" sm="8" class="white--text text-left">
              <h1
                class="font-weight-light mb-2"
                :style="$device.isDesktop ? 'font-size : 45px;': 'font-size : 35px;'"
              >Phần Mềm Khác</h1>
              <h1
                class="font-weight-light"
              >Chúng tôi tự hào mang đến các giải pháp phần mềm chất lượng nhất trong lĩnh vực Marketing giúp cho công việc trở nên dễ dàng hơn.</h1>
              <v-btn outlined href target="_blank" large color="white" class="mt-4">Xem thêm</v-btn>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </v-container>
  </section>
</template>

<style scoped>
#download {
  background-image: url("~@/assets/img/bgDownload.jpg");
  background-attachment: fixed;
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
  height: 500px;
}

#download .container,
#download .row {
  height: 100%;
}
</style>