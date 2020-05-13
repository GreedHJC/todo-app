<template>
    <div>
      <!-- <p>{{ msg }}</p>
      <main v-if="show">메인</main> -->
      <todo-header></todo-header>
      <!-- TODO: TodoInput, TodoList 컴포넌트 등록 -->
        <todo-input v-on:add="addItem"></todo-input>
        <todo-list
                v-bind:propsdata="todoItems"
                v-on:remove="removeItem"
        ></todo-list>
        <todo-footer v-on:clear="clearItems"></todo-footer>
    </div>
</template>

<script>
// import 컴포넌트 이름 from '컴포넌트 파일 경로'
import TodoHeader from './components/TodoHeader.vue';
import TodoInput from './components/TodoInput.vue';
import TodoList from './components/TodoList';
import TodoFooter from './components/TodoFooter'

export default {
    components: {
        // '컴포넌트 이름' : 컴포넌트 내용,
        'todo-header': TodoHeader,
        'todo-input': TodoInput,
        'todo-list': TodoList,
        'todo-footer': TodoFooter,
    },
    data() {
        return {
            todoItems: [],
            inputText: ''
        }
    },
    methods: {
        fetchTodoItems : function() {
            // var arr = [];
            for (var i = 0; i<localStorage.length; i++){
                var value = localStorage.key(i);
                this.todoItems.push(value);
            }
            // return arr;
        },
        clearItems: function() {
            this.todoItems = [];
            localStorage.clear();
        },
        addItem: function(todoItem) {
           this.todoItems.push(todoItem);
            localStorage.setItem(todoItem, todoItem);

        },
        clearInput: function() {
            this.inputText ='';
        },
        removeItem: function(todoItem, index){
            // 배열 변경
            this.todoItems.splice(index, 1);
            // 브라우저 저장소(DB)에서 삭제
            localStorage.removeItem(todoItem)
        }
    },

    created: function() {
        this.fetchTodoItems();
    }

}
</script>

<style>

</style>