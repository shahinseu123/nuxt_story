<script setup>
import { VSkeletonLoader } from 'vuetify/labs/VSkeletonLoader'
const cards = ref([
        {
          title: 'Homemade Dulce de Leche Ice Cream with Chocolate Chips',
          subtitle: 'Happy Foods',
          src: 'https://cdn.vuetifyjs.com/docs/images/graphics/dulce-ice-cream.png',
        },
        {
          title: 'Salted Caramel Swirl Ice Cream',
          subtitle: 'Stone Kitchen',
          src: 'https://cdn.vuetifyjs.com/docs/images/graphics/salted-caramel-ice-cream.png',
        },
        {
          title: 'Peanut Butter No-Churn Ice Cream',
          subtitle: 'The Sweeter Side',
          src: 'https://cdn.vuetifyjs.com/docs/images/graphics/peanut-butter-ice-cream.png',
        },
    ])
const loading = ref(true)  
</script>
<template>
      <v-card
      theme="light"
      max-width="800"
      rounded="lg"
    >
      <v-container>
        <v-row>
          <v-col
            v-for="{ src, title, subtitle } in cards"
            :key="title"
            cols="12"
            md="6"
            lg="4"
          >
            <v-skeleton-loader
              :loading="loading"
              height="240"
              type="image, list-item-two-line"
            >
              <v-responsive>
                <v-img
                  :src="src"
                  class="rounded-lg mb-2"
                  cover
                  height="184"
                ></v-img>

                <v-list-item
                  :title="title"
                  :subtitle="subtitle"
                  class="px-0"
                ></v-list-item>
              </v-responsive>
            </v-skeleton-loader>
          </v-col>
        </v-row>
      </v-container>
           </v-card>
</template>