<script lang="ts">
    import { addTodoEffect, todoAdding } from '../../../../../model/todo/todo.model';


    export let value = '';

    let input: HTMLInputElement;

    $: disabled = $todoAdding;
    $: onSubmit = (event: Event) => {
        event.preventDefault();
        addTodoEffect({ title: value }).then(() => {
            if (input) {
                input.value = '';
            }
        });
    };
</script>

<form class="container" on:submit={onSubmit} class:disabled>
    <div class="form">
        <label class="label" for="create-todo-input">Заголовок</label>
        <input type="text" class="input" id="create-todo-input" bind:value bind:this={input}/>
    </div>
    <button type="submit" class="button">Добавить</button>
</form>

<style lang="scss">
    .container {
        display : flex;
        gap     : 5px;

        .form {
            display        : flex;
            flex-direction : column;
            gap            : 5px;
            flex           : 1;

            .label {
                color     : #777;
                font-size : 14px;
            }

            .input {
                padding : 10px;
                flex    : 1;
            }
        }

        .button {
            padding : 10px;
        }
    }

    .disabled {
        pointer-events : none;
        opacity        : .6;
    }
</style>