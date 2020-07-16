<template>
    <v-container>
        <v-row>
            <v-col>
                temperature (min:-20 max:50)
                <Slider v-model="value1" :min="-20" :max="50" :step="0.1" color="red lighten-1" bg="teal lighten-5" />
            </v-col>
            <v-col>
                humidity (min:0 max:100)
                <Slider v-model="value2" :min="0" :max="100" :step="0.1" color="light-blue lighten-4" bg="teal lighten-5" suffix="%RH" />
            </v-col>
            <v-col>
                readonly (min:0 max:1)
                <Slider v-model="value3" :min="0" :max="1" :step="0.01" color="light-blue lighten-4" bg="teal lighten-5" prefix="VALUE" :readOnly="true" />
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
    import Slider from '@/components/NumSlider'
    export default {
        components: {
            Slider
        },
        data: function () {
            return {
                value1: 0,
                value2: 20,
                value3: 0.5,
            }
        }
    }
</script>