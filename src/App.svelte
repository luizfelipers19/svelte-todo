<script>
    import Form from "./components/Form.svelte";
import Header from "./components/Header.svelte";
    import TodoList from "./components/TodoList.svelte";


    let newText;

    let todos = [
        {id:1 , text: "IDK todo", completed: false},
        {id:2 , text: "IDK todo 3", completed: true},
        {id:3 , text: "My new Todo", completed: true},
    ]

    let totalTodos;
    let remainingTodos;

    $: totalTodos = todos.length;
    $: remainingTodos= todos.reduce((n, todo) => {
        return n+ (todo.completed ? 0 : 1)
    }
    
    ,0)

    function onComplete(event){
        let updateId = event.detail.id;
        // console.log("Completing ", updateId);
        todos.map((todo) =>{
            if (todo.id == updateId) {
                todo.completed = !todo.completed;
            }
        });
        todos = todos;
    }

    function onDelete(event){
        let delId = event.detail.id
        console.log("Deleted the id number ",delId, "Todo");

        todos = todos.filter((todo) => {
            return todo.id != delId
        });
    }

    function createdTodo(){
        console.log("created: ", newText);
        newText =newText.trim();
        if (newText != ""){
            let newId = Math.max(...todos.map((e)=> e.id)) + 1;
            todos = [...todos, {id: newId, text: newText, completed:false}];
         }
         newText = "";
    }

    

    

</script>



<div id="app-container" class="app-container">

    <!-- Header with counter and remaining tasks counter -->
	<Header totalTodos={totalTodos} remainingTodos={remainingTodos}></Header>
	
	<!-- List of actual todos -->
	<TodoList todos= {todos} on:completed={onComplete} on:deleted={onDelete}></TodoList>

    <!-- Form component that takes input from user -->
    <Form bind:newText on:created={createdTodo}></Form>

</div>

<style>
        
        .app-container {
            width: 400px;
            min-height: 500px;
            background-color: #282c34;
            box-shadow: 0 20px 80px rgba(0, 0, 0, 0.6);
            background: radial-gradient(circle, #282c34 0%, rgba(40, 48, 56, 1) 100%);
            position: relative;
            border-radius: 1em;
            padding: 20px;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
        }
        
         ::placeholder {
            opacity: 0.3;
        }

</style>