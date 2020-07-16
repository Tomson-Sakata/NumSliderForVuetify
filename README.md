# NumSliderForVuetify
This is a component that allows you to specify values by sliding.

# Requirement
* Vue 2.6.11
* Vuetify 2.2.11

# Usage
1.copy src/components/NumSlider.vue to your project.

2.Embedded in the components of your project.
    
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

# API

Properties
| name | type | default | desctiption |
| --- |:---:|:---:| --- |
|min|Number|0|Minimum value|
|max|Number|100|Maximum value|
|step|Number|1|Slider movement interval|
|color|String|primary|Slider color|
|bg|String|white|Slider background color|
|readOnly|Boolean|false|Set to read-only status|
