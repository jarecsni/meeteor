<scrollView orientation="vertical" scrollbarIndicatorVisible={false}>
    <stackLayout orientation="vertical">
        {#each events as event}
            {#if !!event.date }
                <label marginLeft=10>{event.date}</label>
            {/if}
            <EventSummary 
                title={event.title}
                time={event.time}
                group={event.group}
            />
        {/each}
    </stackLayout>
</scrollView>

<script>
    import EventSummary from './EventSummary';
    export let events;
</script>