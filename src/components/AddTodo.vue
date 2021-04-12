<template>
    <div>Add todo
        <form @submit="addTodo">
            <input type='text' v-model="title" name='title' placeholder="Add todo. . ." />
            <button type="submit" class="btn">Submit</button>
        </form>
    </div>
</template>

<script>
//import { v4 as uuidv4 } from 'uuid'; no longer requried;
export default {
    name: 'AddTodo',
    methods: {
        addTodo(e){
            e.preventDefault();
            const newTodo = {
            //  id: uuidv4(), fake id
                title: this.title,
                completed: false
            }
            //send up to parent
            this.$emit('add-todo', newTodo);
            this.title = '';
        }
    },
    data() {
        return {
            title: ''
        }
    }
}
//console.log(this.title);
</script>

<style scoped>
    form{
        display: flex;
    }
    input[type="text"]{
        flex: 10;
        padding: 5px;
    }
    button{
        flex: 2;
    }
</style>