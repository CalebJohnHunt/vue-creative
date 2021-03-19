<template>
    <div class='content'>
        <input type='text' placeholder='Swatch name' :class='badName ? "badName" : "normalName"' id='inputName' v-model='name' />
        <div class='color-row' v-for='color in this.colors' :key='color.id'>
            <input class='color-name' type='text' v-model='color.color' :class='color.badName ? "badName" : "normalName"' />
            <div class='color' :style='{"background-color": color.color}'></div>
            <button @click='removeColor(color)'>X</button>
        </div>
        <div class='button-container'>
            <button @click='addColor'>Add Color</button>
            <button @click='addSwatch'>Add Swatch to Palette</button>
        </div>
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
                    ],
        }
    },
    methods: {
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
        addColor() {
            if (this.colors.length > 7)
                return;
            this.colors.push({
                id: this.colors[this.colors.length-1].id+1,
                badName: false,
                color: '#' + (Math.floor(Math.random()*0xeeeeee) + 0x111111).toString(16),
            });
        },
        removeColor(color) {
            if (this.colors.length == 1)
                return;
            let index = this.colors.findIndex(el => el.id == color.id);
            this.colors.splice(index, 1);
        }
    },
    computed: {
    }
}
</script>

<style scoped>
.content {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 70%;

    margin: auto;

    border: 1px solid black;

    border-top-left-radius: 10px;
    border-top-right-radius: 10px;
}

#inputName {
    margin-bottom: 2px;
    /* height: 30px; */
    font-size: 20px;
    max-width: 85%;
    border-top: none;
    border-left: none;
    border-width: 2px;
    border-style: inset;
    border-color: -internal-light-dark(rgb(118, 118, 118), rgb(133, 133, 133));
    border-top-left-radius: 10px;
    border-top-right-radius: 10px;
}

.color-row {
    width: 100%;
    min-height: 50px;

    display: grid;
    grid-template-columns: 30% 60% 10%;
}

.color-name {
    /* border: none; */
    font-size: 18px;
}

.color {
    /* height: 110; */
    width: 100%;
}


.button-container {
    width: 100%;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
}


.badName {
    background-color: lightcoral;
}

.normalName {

}
</style>