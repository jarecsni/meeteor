<page>
    <actionBar title="Meeteor" />
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
        <segmentedBar color='white' class="calendar"
            selectedIndex="{currentCalendar}" on:selectedIndexChange={onCalendarTypeChange}>
            <segmentedBarItem title="Your Groups" />
            <segmentedBarItem title="Going" />
            <segmentedBarItem title="Past" />
        </segmentedBar>
        {#if currentCalendar === 0 }
            <stackLayout orientation="vertical" height="100">
            {#each myUpcomingEvents as event}
                <label margin=10>{event.title}</label>
            {/each}
        </stackLayout>
        {:else if currentCalendar === 1}
            <label margin=10>Nothing coming up...</label>
        {:else}
            <label margin=10>No past yet :)</label>
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

    const myUpcomingEvents = [
        {
            title: 'Bring your Svelte Native project'
        }
    ]
</script>

<style>
    .header {
        font-size: 24px;
    }
    .groupThumbnail {
        background-color: aqua;
    }
    .calendar {
        margin: 5px;
        /* color: yellow;
        selected-background-color: gray;
        background-color: lightskyblue; */
    }
</style>

