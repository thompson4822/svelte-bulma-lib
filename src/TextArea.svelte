<script>
    import { camelCase } from './util/stringManip.js'

    export let disabled = false;
    export let value;
    export let placeholder = '';
    export let label = '';
    export let readonly = false;
    export let isValid = true;
    export let feedback;
    export let required = true;

    $: camelLabel = camelCase(label);

    $: showError = isValid === false && feedback;
</script>

<div class="field">
    <label class="label" for={camelLabel}>{label}</label>
    <div class="control">
            <textarea class="textarea" class:is-danger={!isValid} id={camelLabel} {placeholder} bind:value={value} {required} on:blur {disabled} {readonly}></textarea>
    </div>
    {#if showError}
        <p class="help is-danger">{feedback}</p>
    {/if}
</div>
