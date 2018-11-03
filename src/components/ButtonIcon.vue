<template>
    <div>
        <button @click="sendText" type="button" class="btn btn-info">
            <span :class="Icon"></span> {{Name}}
        </button>

    </div>
</template>

<script>
export default {
    props: {
        Icon: {
            type: String,
            default: 'fa fa-search'
        },
        Name: {
            type: String,
            default: 'Click me'
        },
    },
    methods: {
        sendText () {
            this.$emit('buttonText', 31)

        }
    },
}
</script>

<style scoped>
</style>
