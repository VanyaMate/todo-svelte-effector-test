<script lang="ts">
    import { todoItems, todoLoading } from '../../../../../model/todo/todo.model';
    import TodoItem from '../../../../entity/todo/TodoItem/TodoItem.svelte';
    import RemoveTodoButton from '../../../../feature/todo/RemoveTodoButton/RemoveTodoButton.svelte';
    import UpdateTodoStatusSelect from '../../../../feature/todo/UpdateTodoStatusSelect/UpdateTodoStatusSelect.svelte';
</script>

<section class="container">
    <h2>Список</h2>
    {#if $todoLoading}
        Загрузка...
    {:else}
        {#each $todoItems as todo (todo.id)}
            <TodoItem title={todo.title}>
                <RemoveTodoButton id={todo.id} slot="prefix"/>
                <UpdateTodoStatusSelect id={todo.id} status={todo.status} slot="postfix"/>
            </TodoItem>
        {/each}
    {/if}
</section>

<style>
    .container {
        display        : flex;
        flex-direction : column;
        gap            : 5px;
    }
</style>