<template>
    <form @submit.prevent="submitHandler">
        <input ref="todoItem" v-model="item" type="text">
        <button @click="setTodoList">Add</button>
        <button>Search</button>
    </form>
    <div v-for="(tditem, index) in todoList">
        {{tditem}} <button @click="removeCurrItem(index)">Remove</button>
    </div>
</template>

<script lang="ts" setup>
    const item = useState<String>('item', () => '')
    const todoList = useState<String[]>('todoList', () => ['1','2'])
    const todoItem = ref()

    const setTodoList = () => {
        todoList.value = [...todoList.value, item.value]
        item.value = ''
        todoItem.value.focus()
    }
    const removeCurrItem = (index: number) => {
        todoList.value.splice(index,1)
    }
    const submitHandler = (data: any) => {
        console.log(data)
    }
</script>