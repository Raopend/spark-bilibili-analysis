<template>
    <div class="header">
        <div class="left">
            <span style="font-size: 20px">{{ state.name }}</span>
        </div>
    </div>
</template>

<script setup>
import { reactive, toRefs } from 'vue'
import { useRouter } from 'vue-router'
const router = useRouter()
const pathMap = {
    index: '首页',
    add: '添加商品'
}
const state = reactive({
    name: 'dashboard'
})

router.afterEach((to) => {
    console.log('to', to)
    const { id } = to.query
    state.name = pathMap[to.name]
})
</script>

<style scoped>
.header {
    height: 50px;
    border-bottom: 1px solid #e9e9e9;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 20px;
}
</style>