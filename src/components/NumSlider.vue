<template>
        <div style="position:relative; width:100%; z-index:0" class="mb-1" ref="parent" id="parent">
            <v-progress-linear 
                :value="((editValue - min) / (max - min)) * 100" 
                :min="min" 
                :max="max" 
                height="40" 
                rounded 
                :color="color" 
                :background-color="bg" 
                />
            <v-text-field
                style="position:absolute; width:100%; top:0px; z-index:1"
                v-model.number="editValue"
                v-bind="$attrs"
                hide-details
                outlined 
                dense 
                height="40" 
                type="number" 
                ref="text" 
                class="font-weight-black"
                :readonly="readOnly"
                @focus="!readOnly ? isTextboxFocused=true : isTextboxFocused=false" 
                @blur="isTextboxFocused=false"
                />
            <v-slider
                class="mt-2"
                v-if="isTextboxFocused"
                v-model="editValue"
                :min="min"
                :max="max"
                height="0"
                :readonly="readOnly"
                :step="step"
                :color="color"
                hide-details />
        </div>
</template>

<script>
    export default {
        inheritAttrs: false,
        props: {
            value: {
                type: Number,
                default: 0
            },
            min: {
                type:Number,
                default: 0
            },
            max: {
                type: Number,
                default: 100
            },
            step: {
                type: Number,
                default: 1
            },
            color: {
                type: String,
                default: "primary"
            },
            bg: {
                type: String,
                default: "white"
            },
            readOnly: {
                type: Boolean,
                default: false
            }
        },
        computed: {
            editValue: {
                get: function() {return this.$props.value},
                set: function(v) {
                    if (v == null) {
                        v = ""
                    }
                    this.$emit("input", v)                    
                }
            },
        },
        data: function () {
            return {
                isTextboxFocused: false,
            }
        },
    }
</script>

<style scoped>
    .v-input__slot {
        padding: 0px ! important
    }
</style>