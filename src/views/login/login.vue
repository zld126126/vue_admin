<template>
    <div id="login">
        登录页<el-button>默认按钮</el-button>
        {{ msg }}
    </div>
</template>
<script>
export default {
    name: 'login',
    data(){
        return {
            msg: `这是一个普通的登录页~`
        }
    },
    created(){},
    mounted(){},
    methods:{

    },
    props:{},
    watch:{}
}
</script>
<style lang="scss" scoped>
#login {
    height: 100vh;
    background-color: #344a5f;
}
</style>