<template>
    <DetailViewBase>
        <FormAdd :formSlug="formSlug" :schema="schema" v-if="schema" />
    </DetailViewBase>
</template>


<script lang="ts">
import Vue from "vue"
import FormAdd from "../components/FormAdd.vue"
import DetailViewBase from "../components/DetailViewBase.vue"

export default Vue.extend({
    props: ["formSlug"],
    components: {
        FormAdd,
        DetailViewBase,
    },
    computed: {
        schema() {
            return this.$store.state.formSchema
        },
    },
    async mounted() {
        await this.$store.dispatch("fetchFormSchema", this.formSlug)
    },
})
</script>


<style scoped lang="less">
</style>
