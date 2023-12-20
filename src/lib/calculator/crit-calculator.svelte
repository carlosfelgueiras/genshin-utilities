<script>
    import { Input, Label, Helper } from 'flowbite-svelte';

    let crit = 5;
</script>

<Input type="number" bind:value={crit} />