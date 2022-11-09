<script>
    import Logo from './Logo.svelte';
    import Search from './Search.svelte';
    import Settings from './Settings.svelte';
    import Switch from './Switch.svelte';



</script>

<div class="Header">
    <Logo appName='Aplicación de Notas'/>
    <Search on:input/>
    <Switch/>
    <Settings/>
</div>

<style>

</style>