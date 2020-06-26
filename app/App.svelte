<page>
    <actionBar title="Meeteor" />
    <stackLayout>
        <label class="header" margin=10>Your Groups</label>
        <scrollView orientation="horizontal" scrollbarIndicatorVisible={false}>
            <stackLayout orientation="horizontal" height="170" margin=2>
                {#each myGroups as group}
                    <GroupThumbnail {...group}/>
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
            <EventList events={upcomingEventsGrouped}/>
        {:else if currentCalendar === 1}
            <label margin=10>Nothing coming up...</label>
        {:else}
            <label margin=10>No past yet :)</label>
        {/if}
    </stackLayout>
</page>

<script>
    import { onMount } from 'svelte';
    import GroupThumbnail from './components/GroupThumbnail';
    import EventSummary from './components/EventSummary';
    import EventList from './components/EventList';

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
            name: 'Svelte Natives',
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

    let upcomingEvents = [
        {
            date: '18/06/2020',
            time: '16:00',
            title: 'Some interesting event',
            group: 'React London'
        },
        {
            date: '18/06/2020',
            time: '18:00',
            title: 'Why Svelte is the Best?',
            group: 'Svelte Hackers'
        },
        {
            date: '19/06/2020',
            time: '18:00',
            title: 'Templating with Svelte',
            group: 'Svelte Rookies'
        }
    ];

    function addEvent() {
        upcomingEvents = [...upcomingEvents, {
            date: '19/06/2020',
            time: '20:00',
            title: 'Wonders of Svelte',
            group: 'Svelte Magicians'
        }
        ];
    }

    let upcomingEventsGrouped; 
    $: {
        upcomingEventsGrouped = groupEvents(upcomingEvents);
    }

    function groupEvents(events) {
        const result = [];
        let currentDate = null;
        events.forEach(({date, time, title, group}) => {
            const _date = (date !== currentDate ? date : null);
            result.push({
                time, title, group, date: _date 
            });
            currentDate = date;
        });
        return result;   
    }


</script>

<style>
    .header {
        font-size: 24px;
    }
    .calendar {
        margin: 5px;
        /* color: yellow;
        selected-background-color: gray;
        background-color: lightskyblue; */
    }
</style>

