<page>
    <actionBar title="Meeteor4" />
    <stackLayout>
        <label class="header" margin=10>Your Groups</label>
        <stackLayout orientation="horizontal" height="100">
            {#each myGroups as group}
                <dockLayout backgroundColor="lightgray" margin=10>
                    <label 
                        class="groupThumbnail"  
                        textWrap={true}
                        width=100
                    >
                        {group.name}
                    </label>
                </dockLayout>
            {/each}
        </stackLayout>
        <label class="header" margin=10>Your Calendar</label>
        <segmentedBar selectedBackgroundColor='white' margin="5" 
            selectedIndex="{currentCalendar}" on:selectedIndexChange={onCalendarTypeChange}>
            <segmentedBarItem title="Your Groups" />
            <segmentedBarItem title="Going" />
            <segmentedBarItem title="Past" />
        </segmentedBar>
        {#if currentCalendar === 0 }
            <label>(your groups)</label>
        {:else if currentCalendar === 1}
            <label>(going)</label>
        {:else}
            <label>(past)</label>
        {/if}
    </stackLayout>
</page>

<script>
    let currentCalendar = 0;
    function onCalendarTypeChange(e) {
        currentCalendar = e.value;
    }

    const myGroups = [
        {
            name: 'Sunday Book Club'
        },
        {
            name: 'Svelte Native Hackers'
        },
        {
            name: 'Svelte Stars'
        }
    ];
</script>

<style>
    .header {
        font-size: 24px;
    }
    .groupThumbnail {
        background-color: aqua;
    }
</style>

