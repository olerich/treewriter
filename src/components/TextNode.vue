<template>
<div class='treelevel'>
    <div v-for='(child, index) in nodedata.children' :key='index' class='textnode'>
        <i class="mr-1" :class="{'el-icon-arrow-down': !isCollapsed(index), 'el-icon-arrow-right': isCollapsed(index) }" @click="collapse(index)"></i>
        <p class="editable mr-1" contenteditable="true">{{child.content ? child.content : '(empty)'}}</p>
        <text-node v-if="!isCollapsed(index)" :nodedata='child'></text-node>
    </div>
    <el-button @click="addNode">Add Node</el-button>
</div>
</template>

<style>
.textnode {
    display: flex;
    align-items: center;
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
        collapsed: []
    }),
    methods: {
        addNode(){
            this.nodedata.children.push({content: "", children: []})
        },
        isCollapsed(index) {
            return this.collapsed.includes(index);
        },
        collapse(index){
            const existingIndex = this.collapsed.findIndex(item => item === index);
            if(existingIndex > -1) {
                this.collapsed.splice(existingIndex, 1)
            }
            else {
                this.collapsed.push(index);
            }
        }
    }
}
</script>