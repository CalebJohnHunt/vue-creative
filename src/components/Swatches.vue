<template>
    <div class='content'>
        <div class='swatch-wrapper' v-for='swatch in this.$root.$data.swatches' :key='swatch.id'>
            <div class='swatch' v-for='c in swatch.colors' :key='c' :style='styleBackgroundColor(c)'>
                    {{ c }}
            </div>
        </div>
    </div>
</template>

<script>
export default {
  name: 'Swatches',
  methods: {
      styleBackgroundColor(c) {
          return 'background-color: ' + c;
      }
  }
}
</script>


<style scoped>
.content {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
}

.swatch-wrapper {
    display: flex;
    flex-direction: column;
    min-width: 150px;
    /* width: 40%; */
    max-width: 400px;
}

.swatch {
    color: white;
    text-shadow: -1px -1px 0 #000, 1px -1px 0 #000, -1px 1px 0 #000, 1px 1px 0 #000;
}
</style>