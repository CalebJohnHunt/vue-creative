<template>
    <div class='content'>
        <div class='swatch-wrapper' v-for='swatch in this.$root.$data.swatches' :key='swatch.id'>
            <div class='name'> {{ swatch.name }} </div>
            <div class='swatch' v-for='c in swatch.colors' :key='c' :style='styleBackgroundColor(c)'>
                    {{ c }}
            </div>
            <div class='added-button'>
                <div :class='{ added : swatch.added }'>{{ swatch.added ? 'Yes' : 'No'}} </div>
                <button v-on:click='addSwatch(swatch)'>Add</button>
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
      },
      addSwatch(swatch) {
          swatch.added = !swatch.added;
          if (swatch.added) {
              this.$root.$data.palette.push(swatch);
          } else {
              console.log(this.$root.$data.palette.indexOf(swatch));
              this.$root.$data.palette.splice(this.$root.$data.palette.indexOf(swatch), 1);
          }
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

    margin: 5px 10px;
    border: 1px solid black;
    border-top-left-radius: 10px;
    border-top-right-radius: 10px;
}

.swatch {
    color: white;
    text-shadow: -1px -1px 0 #000, 1px -1px 0 #000, -1px 1px 0 #000, 1px 1px 0 #000;
}

.added-button {
    display: flex;
    flex-direction: row;
}
</style>