<script>
    import TodoItem from "./TodoItem.svelte";

</script>
<!-- List of actual todos -->
<div class="app-body">
    <ul>

        <TodoItem></TodoItem>
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