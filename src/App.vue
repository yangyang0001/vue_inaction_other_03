
<template>
    <div class="root">
        <h1>App根组件, count_from_son is : {{count_from_son}}</h1>
        <Left :msg="message" :student="student"></Left>
        <Right @num_change="change"></Right>
    </div>
</template>

<script>
import Left from '@/components/Left.vue'
import Right from '@/components/Right.vue'

export default {

    components: {
        Left,
        Right,
    },

    data: function () {
        return {
            message: 'Hello Vue.js',
            student: {
                name: 'zhangsan',
                age: 22
            },
            // 定义一个来自子组件的值
            count_from_son: 0
        }
    },

    methods: {
        change: function(val) {
            console.log('change method invoke, val is :' + val);
            this.count_from_son = val;
        },
    },

}
</script>

<style lang="less" scoped>
.root {
    padding: 5px 20px 260px 20px;
    background-color: #b9bdb0;
}
</style>