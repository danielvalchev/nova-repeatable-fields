<template>
    <div>
        <div>
            <input
                :id="subField.name"
                :name="subField.name"
                type="text"
                class="w-full form-control form-input form-input-bordered"
                :class="errorClasses"
                :value="value"
                v-bind="subField.attributes"
                :placeholder="subField.placeholder"
                @input="$emit('input', $event.target.value)"
            />
        </div>
        <p v-if="hasError" class="my-2 text-danger">
            {{ firstError }}
        </p>
    </div>
</template>

<script>
    import {HandlesValidationErrors} from 'laravel-nova'

    export default {

        mixins: [HandlesValidationErrors],

        computed: {
            fieldAttribute() {
                return this.attribute
            },
        },

        props: [
            'subField',
            'value',
            'attribute'
        ],

    }
</script>
