<script context="module">
    export async function preload() {
        let data = {};
        const response = await this.fetch(
            `https://us-central1-pugstagram-co.cloudfunctions.net/data`
        );
        data = await response.json();
        return { data };
    };
</script>

<script>
    import { onMount } from 'svelte';
    import Header from '../components/Header.svelte';
    import Main from '../components/Main.svelte';
    import TimeLine from '../components/TimeLine.svelte';
    import Sidebar from '../components/Sidebar.svelte';
    export let data;
</script>

<svelte:head>
    <title>Doggygram</title>
</svelte:head>

<Main>
    <TimeLine posts={data.posts} />
    <Sidebar {...data.user} />
</Main>