<template>
    <div class='palette'>
        <div class='swatches' v-for='swatch in this.$root.$data.palette' :key='swatch.id'>
            {{ swatch.id }}
        </div>
    </div>
</template>

<script>
export default {
    name: 'Palette',
}
</script>

<style scoped>

</style>