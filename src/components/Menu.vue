<!--  -->
<template>
<div class='language-menu'>
    <div @click="handleToOpen" class="current-language">
        {{currentLanguage}}
    </div>
    <ul v-if="menuShow" class="other-languages">
        <router-link :to="'/'+item.name" tag="li" v-for="(item,index) in otherLanguages" :key="index">{{item.text}}</router-link>
    </ul>
</div>
</template>

<script>
//这里可以导入其他文件（比如：组件，工具js，第三方插件js，json文件，图片文件等等）
//例如：import 《组件名称》 from '《组件路径》';

export default {
//import引入的组件需要注入到对象中才能使用
name:'Menu',
components: {},
data() {
//这里存放数据
return {
    menuShow:false,
    languages:[
        {name:'zh_CN',text:'简体中文'},
        {name:'en_US',text:'English'},
        {name:'es_MX',text:'Español'},
        {name:'de_DE',text:'Deutsch'}
    ]
};
},
//监听属性 类似于data概念
computed: {
    currentLanguage(){
        return this.languages.filter((item)=>item.name===this.$router.history.current.name)[0].text||'';
    },
    otherLanguages(){
        return this.languages.filter((item)=>item.name!==this.$router.history.current.name);
    }
},
//监控data中的数据变化
watch: {},
//方法集合
methods: {
    handleToOpen(){
        this.menuShow=true
    }
},
//生命周期 - 创建完成（可以访问当前this实例）
created() {

},
//生命周期 - 挂载完成（可以访问DOM元素）
mounted() {

},
beforeCreate() {}, //生命周期 - 创建之前
beforeMount() {}, //生命周期 - 挂载之前
beforeUpdate() {}, //生命周期 - 更新之前
updated() {}, //生命周期 - 更新之后
beforeDestroy() {}, //生命周期 - 销毁之前
destroyed() {}, //生命周期 - 销毁完成
activated() {}, //如果页面有keep-alive缓存功能，这个函数会触发
}
</script>
<style  scoped>
.language-menu{
    position:absolute;
    top:15px;
    right:10px;
    min-width:80px;
    background-color:#de335e;
    padding:0 4px;
}
.other-language{
    margin:5px 0;
}
.other-language li{
    padding:3px 0;
}

</style>