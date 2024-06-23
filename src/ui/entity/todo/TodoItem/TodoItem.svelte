<script>
    export let title = '';
</script>

<article class="container">
    <slot name="prefix"/>
    <h3 class="title">{title}</h3>
    <slot name="postfix"/>
</article>

<style lang="scss">
    .container {
        padding       : 5px;
        border        : 1px solid #aaa;
        border-radius : 5px;
        display       : flex;
        gap           : 5px;
        align-items   : center;

        .title {
            flex : 1;
        }
    }
</style>