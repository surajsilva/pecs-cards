<template>
  <div
    class="v-card"
    :style="{
      width: width + 'px',
      height: height + 'px',
      border: '3px solid grey'
    }"
  >
    <div
      class="v-card__image"
      :style="{
        height: (height - textHeight - 1) + 'px'
      }"
    >
      <img :src="imageSrc" :alt="imageAlt" style="width: 100%; height: 100%;" />
    </div>
    <div
      class="v-card__text"
      :style="{
        height: textHeight + 'px',
        marginTop: '1px'
      }"
    >
      <div
        class="v-card__text-content"
        style="display: flex; align-items: center; justify-content: center;"
      >
        {{ text }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'VCard',
  props: {
    imageSrc: {
      type: String,
      default: '../img/cars.jpg'
    },
    imageAlt: {
      type: String,
      default: ''
    },
    text: {
      type: String,
      required: true
    },
    width: {
      type: Number,
      default: 275
    },
    height: {
      type: Number,
      default: 275
    }
  },
  computed: {
    textHeight() {
      return 40;
    }
  }
}
</script>

<style scoped>
/* Add any custom styles here */
</style>
