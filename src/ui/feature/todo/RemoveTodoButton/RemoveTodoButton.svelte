<script>
    import {removeTodoEffect, todoItemsPendingStatus} from "../../../../model/todo/todo.model";

    export let id;

    $: disabled = $todoItemsPendingStatus[id];
</script>

{#if id}
    <button class="container" class:disabled on:click={() => removeTodoEffect(id)}>Удалить</button>
{/if}

<style>
    .container {
        padding : 5px;
    }

    .disabled {
        pointer-events : none;
        opacity        : .6;
    }
</style>