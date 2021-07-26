<template>
<div class='treelevel'>
    <div v-for='(child, index) in nodedata.children' :key='index' class='textnode'>
        <i @click="collapse">c</i>
        <p class="editable" contenteditable="true">{{child.content ? child.content : '(empty)'}}</p>
        <text-node v-if="!collapsed" :nodedata='child'></text-node>
    </div>
    <el-button @click="addNode">Add Node</el-button>
</div>
</template>

<style>
.textnode {
    display: flex;
}

.treelevel {
    margin-top: 1rem;
    display: flex;
    flex-direction: column;
    align-content: flex-start;
}
</style>

<script>

export default {
    name: 'text-node',
    props: {
        nodedata: Object
    },
    data: () => ({
        collapsed: true
    }),
    methods: {
        addNode(){
            this.nodedata.children.push({content: "", children: []})
        },
        collapse(){
            this.collapsed = !this.collapsed
        }
    }
}
</script>