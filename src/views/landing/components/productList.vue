<template>
  <div class="row">
    <div class="col-12 col-sm-6 col-md-4 col-lg-3 p-2" v-for="(item, index) in products">
      <q-card>
        <q-img :src="item.thumbnail" />

        <!-- <q-card-section>
          <q-btn
            fab
            color="primary"
            icon="place"
            class="absolute"
            style="top: 0; right: 12px; transform: translateY(-50%)"
          />

          <div class="row no-wrap items-center">
            <div class="col text-h6 ellipsis">{{ item.title }}</div>
            <div class="col-auto text-grey text-caption q-pt-md row no-wrap items-center">
              <q-icon name="place" />
              250 ft
            </div>
          </div>

          <q-rating v-model="item.rating" :max="5" size="32px" />
        </q-card-section> -->

        <q-card-section class="pt-3">
          <div class="text-subtitle1 text-xl font-bold">$ {{ item.price }}</div>
          <div class="text-caption text-grey">{{ item.description }}</div>
        </q-card-section>

        <q-separator />

        <q-card-actions>
          <q-btn flat round icon="event" />
          <q-btn flat color="primary"> Reserve </q-btn>
        </q-card-actions>
      </q-card>
    </div>
  </div>
</template>
<script setup>
import axios from "axios";
import { ref } from "vue";

const products = ref([]);
async function init() {
  const { data } = await axios.get("https://dummyjson.com/products");
  products.value = data.products;
  console.log(data);
}
init();
</script>
