<template>
    <div>
        <input title="Search" @input="onInput"/>
    </div>
</template>

<script type="text/javascript">
    export default {
        name: 'SearchBar',
        methods: {
            onInput: function (event) {

                // 父組件使用 props 傳遞數據給子組件
                // 子組件使用 $emit 觸發父組件事件
                this.$emit('termChange', event.target.value);
            }
        }
    };
</script>

<style>

</style>