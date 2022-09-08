<script>
  export default {
    data() {
      return {
        newTodoText: '',
        newTodoTitle:'',
        todos: [],
      }
    },
    methods: {
      addTodo() {
        if(this.newTodoTitle === '') {
          alert('タイトルを入力してください')
          return 
        }else if(this.newTodoText === ''){
          alert('本文を入力してください')
          return 
        }
        this.todos.push({
          isDone: false,
          title: this.newTodoTitle,
          text: this.newTodoText,
        })
        this.newTodoText = ''
        this.newTodoTitle = ''
      },
    },
  }
  </script>
  
  <template>
    <h1>My ToDo App</h1>
    <input type="text" v-model="newTodoTitle" />
    <input type="text" v-model="newTodoText" /><button @click="addTodo">追加</button><button>完了済みを削除する</button>
    <p v-if="todos.length === 0">ToDoがまだありません！</p>
    <ul v-else>
      <li v-for="todo in todos">
        <input type="checkbox" /><span>{{ todo.text }}</span>
      </li>
    </ul>
  </template>
  
  <style>
  body {
    background-color: #eee;
  }
  
  .todo-done {
    text-decoration: line-through;
  }
  </style>