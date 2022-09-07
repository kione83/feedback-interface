<script>
    export let style = "primary";
    export let type = "button";
    export let disabled = false;
</script>

<button {type} {disabled} class={style}>
    <slot />
</button>

<style>
    button {
        color: #fff;
        border: 0;
        border-radius: 8px;
        color: #fff;
        width: 100px;
        height: 40px;
        cursor: pointer;
    }
    .primary {
        background-color: #202142;
    }
    .secondary {
        background: #a5091e;
    }
    button:hover {
        transform: scale(0.98);
        opacity: 0.9;
    }
    button:disabled {
        background-color: #cccccc;
        cursor: auto;
        color: #333;
    }
    button:disabled:hover {
        transform: scale(1);
        opacity: 1;
    }
</style>
