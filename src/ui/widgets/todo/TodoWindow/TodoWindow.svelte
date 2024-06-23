<script>
    import {onMount} from "svelte";
    import {loadTodosEffect} from "../../../../model/todo/todo.model";
    import TodoHeader from "./TodoHeader/TodoHeader.svelte";
    import TodoList from "./TodoList/TodoList.svelte";

    onMount(loadTodosEffect);
</script>

<div class="container">
    <TodoHeader/>
    <TodoList/>
</div>

<style>
    .container {
        display        : flex;
        flex-direction : column;
        gap            : 20px;
        width          : 600px;
        height         : calc(100dvh - 20px);
        margin         : 10px auto;
        padding        : 10px;
        border-radius  : 10px;
    }
</style>