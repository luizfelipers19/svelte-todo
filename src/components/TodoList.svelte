<script>
    import TodoItem from "./TodoItem.svelte";

</script>
<!-- List of actual todos -->
<div class="app-body">
    <ul>

        <TodoItem itemText="First ToDo" completed = {true}></TodoItem>
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