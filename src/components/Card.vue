<template>
  <v-card class="card" :width="cardWidth" :height="cardHeight" border>
    <v-card-title class="image" :style="{ height: `${imageHeight}px` }">
      <v-img :src="getUrl(cardImg)" :style="{ transform: `rotate(${trf}deg)` }" contain height="100%"></v-img>
    </v-card-title>
    <v-card-text class="text" :style="{ fontSize: '12px', height: '40px', display: 'flex', alignItems: 'center', justifyContent: 'center', marginTop: '1px' }">
      <span>{{ cardTxt }}</span>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  name: "VCard",
  props: {
    cardWidth: {
      type: Number,
      default: 200,
    },
    cardHeight: {
      type: Number,
      default: 200,
    },
    cardImg: {
      type: String
    },
    cardTxt: {
      type: String
    },
    trf: {
      type: Number,
      default: 0
    }
  },
  data() {
    return {
      imageHeight: this.cardHeight - 40,
    };
  },
  methods: {
    getUrl(u) {
      return new URL(u, import.meta.url).href
    }
  }
};

// dataUrl(){
//         return 'data:image/jpeg;base64,' + btoa(
//             new Uint8Array(this.info.image)
//             .reduce((data, byte) => data + String.fromCharCode(byte), '')
//         );
//     }
</script>

<style scoped>
.card {
  border: 3px solid grey;
}
.image {
  padding: 0;
  margin-bottom: 1px;
}
</style>
