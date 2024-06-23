<script lang="ts">
    import { DomainTodoStatus } from '../../../../types/todo/todo.type';
    import { todoItemsPendingStatus, updateTodoEffect } from '../../../../model/todo/todo.model';


    export let id;
    export let status: DomainTodoStatus;
    $: disabled = $todoItemsPendingStatus[id];

    $: onChange = function (event: Event) {
        if (id && event.target) {
            updateTodoEffect([ id, { status: +(event.target as HTMLSelectElement).value as DomainTodoStatus } ]);
        }
    };
</script>

<select value={status} on:change={onChange} class="container" class:disabled>
    <option value={DomainTodoStatus.AWAIT}>Ожидает</option>
    <option value={DomainTodoStatus.IN_PROGRESS}>В процессе</option>
    <option value={DomainTodoStatus.DONE}>Завершено</option>
</select>

<style>
    .container {
        padding : 5px;
    }

    .disabled {
        pointer-events : none;
        opacity        : .6;
    }
</style>