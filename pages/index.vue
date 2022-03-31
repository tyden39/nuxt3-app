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
    const item = useState<string>('item', () => '')
    const todoList = useState<string[]>('todoList', () => ['1','2'])
    const todoItem = ref()
    const originList = useState<string[]>('originList', () => todoList.value)

    const searchList = () => {
        todoList.value = todoItem.value.filter
    }

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