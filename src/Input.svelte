<script>
    import { camelCase } from './util/stringManip.js'
    export let disabled = false;
    export let feedback;
    export let icon = null;
    export let isValid = true;
    export let label;
    export let max = 10;
    export let maxlength = 0;
    export let min = 0;
    export let pattern = '';
    export let placeholder = "";
    export let readonly = false;
    export let required = true;
    export let size = 200;
    export let step = 1;
    export let type = "text";
    export let value;

    $: camelLabel = camelCase(label || placeholder);

    $: showError = isValid === false && feedback;

    $: hasIcon = ['password', 'email', 'date', 'search', 'time'].includes(type) || icon

</script>

<div class="field">
    {#if label}
        <label class="label" for={camelLabel}>{label}</label>
    {/if}
    <div class="control" class:has-icons-left={hasIcon}>
        {#if type === 'text'}
            <input type="text" class="input" class:is-danger={!isValid} id={camelLabel} {placeholder} bind:value={value} {required} on:blur {disabled} {readonly}>
            {#if icon}
                <span class="icon is-small is-left"><i class="fas {icon}"></i></span>
            {/if}

        {:else if type === 'email'}
            <input type="email" class="input" class:is-danger={!isValid} id={camelLabel} {placeholder} bind:value={value} {required} on:blur {disabled} {readonly}>
            <span class="icon is-small is-left"><i class="fas fa-envelope"></i></span>

        {:else if type === 'password'}
            <input type="password" class="input" class:is-danger={!isValid} id={camelLabel} {placeholder} bind:value={value} {required} on:blur {disabled} {readonly}>
            <span class="icon is-small is-left"><i class="fas fa-lock"></i></span>
    
        {:else if type === 'date'}
            <input type="date" class="input" class:is-danger={!isValid} id={camelLabel} {placeholder} bind:value={value} {required} on:blur {disabled} {readonly}>
            <span class="icon is-small is-left"><i class="fas fa-calendar-alt"></i></span>
    
        {:else if type === 'datetime-local'}
            <input type="datetime-local" class="input" class:is-danger={!isValid} id={camelLabel} {placeholder} bind:value={value} {required} on:blur {disabled} {readonly}>
        
        {:else if type === 'file'}
            <input type="file" class="input" class:is-danger={!isValid} id={camelLabel} {placeholder} bind:value={value} {required} on:blur {disabled} {readonly}>
    
        {:else if type === 'image'}
            <input type="image" class="input" class:is-danger={!isValid} id={camelLabel} {placeholder} bind:value={value} {required} on:blur {disabled} alt={label} {readonly}>
        
        {:else if type === 'month'}
            <input type="month" class="input" class:is-danger={!isValid} id={camelLabel} {placeholder} bind:value={value} {required} on:blur {disabled} {readonly}>

        {:else if type === 'number'}
            <input type="number" class="input" class:is-danger={!isValid} id={camelLabel} {placeholder} bind:value={value} {required} on:blur {disabled} {readonly}>

        {:else if type === 'search'}
            <input type="search" class="input" class:is-danger={!isValid} id={camelLabel} {placeholder} bind:value={value} {required} on:blur {disabled} {readonly}>
            <span class="icon is-small is-left"><i class="fas fa-search"></i></span>

        {:else if type === 'tel'}
            <input type="tel" class="input" class:is-danger={!isValid} id={camelLabel} {placeholder} bind:value={value} {required} on:blur {disabled} {readonly}>

        {:else if type === 'time'}
            <input type="month" class="input" class:is-danger={!isValid} id={camelLabel} {placeholder} bind:value={value} {required} on:blur {disabled} {readonly}>
            <span class="icon is-small is-left"><i class="fas fa-clock"></i></span>

        {:else if type === 'url'}
            <input type="url" class="input" class:is-danger={!isValid} id={camelLabel} {placeholder} bind:value={value} {required} on:blur {disabled} {readonly}>
            {#if icon}
                <span class="icon is-small is-left"><i class="fas {icon}"></i></span>
            {/if}

        {:else if type === 'week'}
            <input type="week" class="input" class:is-danger={!isValid} id={camelLabel} {placeholder} bind:value={value} {required} on:blur {disabled} {readonly}>

        {/if}
    </div>
    {#if showError}
        <p class="help is-danger" id="{camelLabel}-feedback">{feedback}</p>
    {/if}
</div>
