<script>
    export let title;
    export let isActive=false;

</script>

<style>

</style>

<div class="modal" class:is-active={isActive}>
    <div class="modal-background"></div>
    <div class="modal-card">
        <header class="modal-card-head">
            <p class="modal-card-title">{title}</p>
            <button class="delete" aria-label="close"></button>
        </header>
        <section class="modal-card-body">
            <slot name="content"></slot>
        </section>
        <footer class="modal-card-foot">
            <slot name="footer"></slot>
        </footer>
    </div>
</div>