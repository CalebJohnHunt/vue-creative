<template>
    <div class='palette'>
        <div class='swatch' v-for='swatch in this.$root.$data.palette' :key='swatch.id'>
            <div class='name'>
                <h1>{{ swatch.name }}</h1>
            </div>
            <div class='color-wrapper'>
                <div class='color' v-for='color in swatch.colors' :key='color' :style='{"background-color": color, width: 100/swatch.colors.length + "%"}'></div>
            </div>
            <button class='removeButton' @click='removeSwatch(swatch)'>X</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Palette',
    methods: {
        removeSwatch(swatch) {
            let index = this.$root.$data.palette.findIndex(el => el.id == swatch.id);
            if (swatch.added) swatch.added = false;
            this.$root.$data.palette.splice(index, 1);
        }
    }
}
</script>

<style scoped>
.swatch {
    display: grid;
    margin: 10px 0;
    /* border: 1px solid black; */
    grid-template-columns: 10% 80% 10%;
    grid-template-areas: "name colors button";
}

.name {
    grid-area: "name";
    word-wrap: break-word;
    /* width: 400px; */
}

h1 {
    font-size: 15px;
}

.color-wrapper {
    grid-area: colors;
    display: flex;
    flex-direction: row;
    width: 100%;
}

.color {
}

.removeButton {
    grid-area: button;
}
</style>