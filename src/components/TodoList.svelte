<script>
    import { createEventDispatcher } from "svelte";
    import TodoItem from "./TodoItem.svelte";
    export let todos;
    const dispatch = createEventDispatcher();

    function forward(event){
        // console.log("in todos: ", event.detail);
        dispatch("completed", event.detail);
    }

</script>
<!-- List of actual todos -->
<div class="app-body">
    <ul>

       {#each todos as todo}
        <TodoItem 
            itemId = {todo.id}
            itemText= {todo.text} 
            completed = {todo.completed}
            on:completed= {forward}>
        
        </TodoItem>
       {/each}
        <TodoItem itemText="Second ToDo" completed = {true}></TodoItem>
        <TodoItem itemText="Incompleted ToDo" completed = {false}></TodoItem>
        <TodoItem></TodoItem>
        <TodoItem></TodoItem>


    </ul>

    
</div>

<style>

        ul {
            list-style-type: none;
            -webkit-padding-start: 0;
            padding-left: 0px;
        }
        
        .app-body {
            flex-grow: 1;
            max-height: 600px;
            overflow-x: hidden;
        }
        
        
        
         ::placeholder {
            opacity: 0.3;
        }
        
</style>