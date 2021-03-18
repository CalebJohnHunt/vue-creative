<template>
    <div class='palette'>
        <div v-for='swatch in this.$root.$data.palette' :key='swatch.id'>
            <div v-for='color in swatch.colors' :key='color'>
                {{ color }}
            </div>
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