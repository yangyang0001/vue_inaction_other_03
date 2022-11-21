<template>
    <div class="right">
        <h3>Right组件</h3>
        <p>count is: {{count}}</p>
        <button @click="handleAdd">+1</button> 
        &nbsp;&nbsp;
        <button @click="handleDel">-1</button>
        <p>来自Left.vue的数据 message_from_left is: {{message_from_left}}</p>

    </div>
</template>

<script>
import bus from '@/eventBus.js'

export default {
    data() {
        return {
            count: 0,
            message_from_left: ''
        }
    },
    methods: {
        handleAdd: function() {
            this.count++;
            this.$emit('num_change', this.count);
        },
        handleDel: function() {
            this.count--
            this.$emit('num_change', this.count);
        }
    },

    mounted() {
        var _this = this;
        bus.$on('send_message_to_right', function(val) {
            console.log('right.vue’s message_from_left is:' + val);
            _this.message_from_left = val;
        });
    }
}
</script>

<style lang="less" scoped>
.right {
    float: right;
    background-color: #e0e30e;
    padding: 5px 0px 20px 20px;
    font-weight: bolder;
    width: 48%;
}
</style>