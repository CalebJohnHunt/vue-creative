<template>
    <div class='content'>
        <div class='swatch' v-for='color in this.colors' :key='color.id'>
            <div class='color' :style='styleBackgroundColor(color.color)'>Hello</div>
            <input type='text' v-model='color.color' />
        </div>
    </div>
</template>

<script>
export default {
    name: 'Create',
    data: () => {
        return {
            colors: [
                        {
                            id: 1,
                            color: '#aa00ff',
                        },
                        {
                            id: 2,
                            color: '#aa00ff'
                        } 
                    ],
        }
    },
    methods: {
        styleBackgroundColor(c) {
            return 'background-color: ' + c;
        },
    }
}
</script>

<style scoped>

</style>