<template>
<div>
    <tree :treeData="testdata"></tree>
</div>
    
</template>

<script>
import vue from 'vue'
import tree from '@/components/tree'
vue.component('tree',tree); 
export default {
    name:'test',
    data(){
        return{
            testdata:[
                {
                    name:"一级菜单",
                    children:[
                        {
                            name:'二级菜单',
                            children:[
                                {
                                    name:'三级菜单'
                                },
                                {
                                    name:'三级菜单'
                                }
                            ]
                        },
                        {
                            name:'二级菜单',
                            children:[
                                {
                                    name:'三级菜单',
                                    children:[
                                        {
                                            name:'四级菜单'
                                        },
                                        {
                                            name:'四级菜单'
                                        },
                                        {
                                            name:'四级菜单'
                                        }
                                    ]
                                },
                                {
                                    name:'三级菜单',
                                    children:[
                                        {
                                            name:'四级菜单',
                                        }
                                    ]
                                }
                            ]
                        },
                        {
                            name:'二级菜单',
                            children:[
                                {
                                    name:'三级菜单'
                                },
                                {
                                    name:'三级菜单'
                                }
                            ]
                        }
                    ]
                }
            ]
        }
    }
}
</script>

<style>

</style>

