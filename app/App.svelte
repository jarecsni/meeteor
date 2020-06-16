<page>
    <actionBar title="Meeteor2" />
    <stackLayout>
        <label class="header" margin=10>Your Groups</label>
        <scrollView orientation="horizontal">
            <stackLayout orientation="horizontal" height="170" margin=2>
                {#each myGroups as group}
                    <absoluteLayout backgroundColor="lightgray" margin=4>
                        <image 
                            src={group.thumbnail}
                            width="100"
                            height="100"
                            top=0
                        />
                        <label 
                            class="groupThumbnail"  
                            textWrap={true}
                            width=100
                            height=170
                            top=40
                            marginLeft=4
                        >
                            {group.name}
                        </label>
                    </absoluteLayout>
                {/each}
            </stackLayout>
        </scrollView>
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
            name: 'Sunday Book Club',
            thumbnail: 'https://bookofaces.files.wordpress.com/2019/02/ck-jhbsun081fshcr.jpg?w=256&h=256&crop=1'
        },
        {
            name: 'Svelte Native Hackers',
            thumbnail: 'https://twobluecommunications.com/wp-content/uploads/2018/12/Chelsea-Waterfront-3-256x256.jpg'
        },
        {
            name: 'Svelte Stars',
            thumbnail: 'https://twobluecommunications.com/wp-content/uploads/2018/06/Eastward-view-cropped-bottom-downsized-256x256.jpg'
        },
        {
            name: 'Svelte Life',
            thumbnail: 'https://twobluecommunications.com/wp-content/uploads/2018/06/Eastward-view-cropped-bottom-downsized-256x256.jpg'
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
        opacity: 1;
    }
    .calendar {
        margin: 5px;
        /* color: yellow;
        selected-background-color: gray;
        background-color: lightskyblue; */
    }
</style>

