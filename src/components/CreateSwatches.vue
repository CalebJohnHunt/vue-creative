<template>
    <div class='content'>
        <input type='text' placeholder='Swatch name' :class='badName ? "badName" : "normalName"' id='inputName' v-model='name' />
        <div class='swatch' v-for='color in this.colors' :key='color.id'>
            <div class='color' :style='styleBackgroundColor(color.color)'>Hello</div>
            <input type='text' v-model='color.color' :class='color.badName ? "badName" : "normalName"' />
        </div>
        <button @click='addSwatch'>Add</button>
    </div>
</template>

<script>
export default {
    name: 'CreateSwatches',
    data: () => {
        return {
            badName: false,
            name: '',
            colors: [
                        {
                            id: 1,
                            badName: false,
                            color: '#aa00ff',
                        },
                        {
                            id: 2,
                            badName: false,
                            color: '#aa00ff',
                        },
                        {
                            id: 3,
                            badName: false,
                            color: '#aa00ff',
                        },
                        {
                            id: 4,
                            badName: false,
                            color: '#aa00ff',
                        },
                        {
                            id: 5,
                            badName: false,
                            color: '#aa00ff',
                        },
                        {
                            id: 6,
                            badName: false,
                            color: '#aa00ff',
                        }
                    ],
        }
    },
    methods: {
        styleBackgroundColor(c) {
            return 'background-color: ' + c;
        },
        addSwatch() {
            // We only update badName here because we don't want the field to be red until they attempt to submit
            this.badName = !this.name; // badName = we don't have a name

            // check to make sure each color is appropriate
            let colorFail = false;
            for (let c of this.colors) {
                if (!/^#[0-9a-fA-F]{6}$/.test(c.color)) { // regex: #[hex char]{6 times}
                    c.badName = true;
                    colorFail = true;
                } else {
                    c.badName = false;
                }
            }

            // If there's a bad color name or no swatch name, just return early
            if (colorFail || this.badName)
                return;
            
            this.$root.$data.palette.push({
                // The prefab swatches have .added, but that's just a remnant of how we add keep track of which ones we've added
                id: this.$root.$data.userGeneratedID++, // increase id at the same time so we don't get duplicate ids
                name: this.name,
                colors: this.colors.map(el => el.color),
            });
        },
    },
    computed: {
    }
}
</script>

<style scoped>
#inputName {

}

.badName {
    background-color: lightcoral;
}

.normalName {

}
</style>