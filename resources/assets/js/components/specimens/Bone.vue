<template>
    <div>
        <v-autocomplete v-model="sb_id" :key="sb_id" :label="label" placeholder="Select Bone" :dusk="dusk"
                        :items="items" item-text="name" item-value="id"
                        :required="required" :rules="rules" :disabled="disabled">
        </v-autocomplete>
    </div>
</template>
<script>
    import {mapGetters, mapState} from "vuex";

    export default {
        name: "Bone",
        props: {
            value: { type: [Number, String], default: null },
            name: { type: String, default: "sb_id" },
            label: { type: String, default: "Bone" },
            dusk: { type: String, default: "se-bone" },
            disabled: { type: Boolean, default: false },
            required: { type: Boolean, default: true },
        },
        data() {
            return {
                sb_id: this.value,
            };
        },
        watch: {
            value(val) {
                this.sb_id = val;
            },
            sb_id(val) {
                this.$emit("input", val);
            }
        },
        computed: {
            ...mapState({
                //
            }),
            ...mapGetters({
                items: 'getBones',
            }),
            rules() {
                return (this.required) ? [() => !!this.sb_id || 'Bone is required'] : [];
            }
        },
    };
</script>
<style scoped>
</style>
