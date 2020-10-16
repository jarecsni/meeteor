<scrollView orientation="vertical" scrollbarIndicatorVisible={false}>
    <stackLayout orientation="vertical">
        {#each events as event}
            <EventSummary {...event}/>
        {/each}
    </stackLayout>
</scrollView>

<script>
import App from '~/App.svelte';
    import EventSummary from './EventSummary';
    export let events;
</script>