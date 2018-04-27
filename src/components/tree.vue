<template>
    <div class="l_tree_container">
        <tree-item :model="treeData"></tree-item>
    </div>
</template>


<script>
    import Vue from 'vue'
    // 树组件
    Vue.component('tree-item',{
        template:`
        <ul class="l_tree">
            <li class="l_tree_branch" v-for="item in model">
                <div class="l_tree_click">
                    <button type="button" class="l_tree_children_btn" v-if="item.children"  @click="toggle(item)">{{ !item.show ? '-' : '+' }}</button>
                    <span class="l_folder">{{ item.name }}</span>
                </div>
                <tree-item v-show="!item.show" v-if="item.children" :model="item.children"></tree-item>
            </li>
        </ul>`,
        props:{
            model:{}
        },
        methods:{
           toggle:function(item){
               var idx = this.model.indexOf(item)
               Vue.set(this.model[idx], 'show', !item.show)
           }
        }
    });

    export default {
        name:'l_tree',
        props:{
            treeData:{}
        }
    }
</script>

<style>
    /* 
* 功能:tree组件样式
*/
ul,li{
    list-style:none;
}
.l_tree_container{
    width: 100%;
    height: 100%;
    box-shadow: 0 0 3px #ccc;
    margin: 13px;
    position: relative;
}
.l_tree{
    width: calc(100% - 26px);
    height: 100%; 
}
.l_tree_branch{
    width: 100%;
    height: 100%;
    display: block;
    padding: 13px;
    position: relative;
}
.l_tree_branch .l_tree_children_btn{
    width: 19px;
    height: 19px;
    background-color: #23b1f0;
    font-size: 14px;
    text-align: center;
    color: #ffffff;
    outline: none;
    border: 0;
    cursor: pointer;
}
ul.l_tree:before{
    content: '';
    border-left: 1px dashed #999999;
    height: calc(100%);
    position: absolute;
    left: 10px;
    top: 0px;
}
.l_tree .l_tree_branch:last-child::before{
    content: '';
    width: 3px;
    height: calc(100% - 24px);
    display: block;
    background-color:#fff;
    position: absolute;
    bottom: 0;
    left: -31px;

}

.l_tree,.l_tree_branch{
    position: relative;
}
.l_tree_branch::after{
    content: '';
    width: 40px;
    height: 0;
    border-bottom: 1px dashed #000;
    position: absolute;
    right: calc(100% - 12px);
    top: 23px;
}

.l_tree_container > .l_tree::before,
.l_tree_container > .l_tree > .l_tree_branch::after
{
    display: none;
}
</style>

