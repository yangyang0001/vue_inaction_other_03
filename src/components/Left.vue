<template>
    <div class="left">
        <h3>Left组件</h3>
        <p>msg is : {{msg}}</p>
        <p>student is : {{student}}</p>
        <p>左侧数据 message is: {{message}}</p>
        <button @click="send_message_to_right">发送数据到Right</button>
    </div>
</template>

<script>

import bus from '@/eventBus.js'

export default {

    props: ['msg', 'student'],

    data() {
        return {
            init: 9,
            message: '黑云压城城欲摧, 渚清沙白鸟飞回。借问酒家何处有, 一枝红杏出墙来。'
        }
    },

    methods: {
        send_message_to_right: function() {
            bus.$emit('send_message_to_right', this.message);
        }
    },

    mounted() {

    }

}

</script>

<style lang="less" scoped>
.left {
    float: left;
    background-color: aqua;
    padding: 5px 0px 20px 20px;
    font-weight: bolder;
    width: 48%;
}
/deep/ h5 {
    color: red;
}
</style>