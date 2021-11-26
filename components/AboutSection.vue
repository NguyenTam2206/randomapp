<template>
  <section id="about">
    <v-container fluid>
      <v-row align="center" justify="center">
        <v-col cols="10">
          <v-row align="center" justify="center">
            <v-col cols="12" md="7">
              <h1
                class="font-weight-light mb-4"
                :style="$device.isDesktop ? 'font-size : 45px;': 'font-size : 35px;'"
              >Các bước sử dụng</h1>
              <v-row>
                <v-col cols="12" class="d-flex align-center">
                  <v-icon color="secondary" class="mr-4" size="50">mdi-numeric-1-circle-outline</v-icon>
                  <div class="text-justify" style="font-size : 20px;">
                    Chọn số thứ tự nhỏ nhất, sau đó
                    chọn số thứ tự lớn nhất đúng với nhu cầu của bạn.
                  </div>
                </v-col>
                <v-col cols="12" class="d-flex align-center">
                  <v-icon color="secondary" class="mr-4" size="50">mdi-numeric-2-circle-outline</v-icon>
                  <div
                    class="text-justify"
                    style="font-size : 20px;"
                  >Bấm nút Quay Ngay, kết quả sẽ xuất hiện ngẫu nhiên trong khoảng từ số nhỏ nhất đến số lớn nhất, bao gồm cả 2 số mốc.</div>
                </v-col>
                <v-col cols="12" class="d-flex align-center">
                  <v-icon color="secondary" class="mr-4" size="50">mdi-numeric-3-circle-outline</v-icon>
                  <div
                    class="text-justify"
                    style="font-size : 20px;"
                  >Trao phần thưởng cho khách hàng may mắn. Tiếp tục quay số.</div>
                </v-col>
              </v-row>
            </v-col>
            <v-col cols="12" md="5" class="d-none d-md-flex">
              <v-img
                :src="require('@/assets/img/ill1.svg')"
                class="d-block ml-auto mr-auto"
                max-width="400px"
              />
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </v-container>
  </section>
</template>

<style scoped>
#about {
  background-color: #f4f7f5;
}
</style>
