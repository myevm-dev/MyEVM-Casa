<script>
    import Sidebar from './Sidebar.svelte';
    import Routes from './Routes.svelte';
    import BackToTopButton from './scrollToTop.svelte';
</script>
  
<main>
    <div class="main-content">
        <Sidebar />
        <Routes />
    </div>
    <BackToTopButton />
</main>

<style>
    main {
        width: 100%;
        display: flex;
        flex-direction: column;
        padding: 1em;
        box-sizing: border-box;
        gap: 3em;
    }
</style>