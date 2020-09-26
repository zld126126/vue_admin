<template>
    <div id="login">
        <div class="login-wrap">
            <ul class="menu-tab">
                <li v-for="item in menuTabs" v-bind:key="item.id" v-bind:class="{'current':item.current}" @click="toggleMenu(item)">{{ item.txt}}</li>
            </ul>
        </div>
    </div>
</template>
<script>
export default {
    name: 'login',
    data(){
        return {
            menuTabs:[
                {txt:'登录',current:true},
                {txt:'注册',current:false}
            ]
        }
    },
    created(){},
    mounted(){},
    methods:{
        toggleMenu(data){
            this.menuTabs.forEach(elem => {
                elem.current = false
            });
            data.current = true
        }
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
.login-wrap {
    width: 330px;
    margin: auto;
}
.menu-tab {
    text-align: center;
    li {
        display: inline-block;
        width: 88px;
        line-height: 36px;
        font-size: 14px;
        color:white;
        border-radius: 2px;
        cursor: pointer;
    }
    .current {
        background-color: rgba(0,0,0,0.1);
    }
}
</style>