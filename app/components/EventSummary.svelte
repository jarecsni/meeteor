{#if !!date }
    <label marginLeft=10>{date}</label>
{/if}
<label marginLeft=10>{time}</label>
<label marginLeft=10>{title}</label>
<label marginLeft=10 marginBottom=10>{group}</label>

<script>
    export let date, time, title, group
</script>