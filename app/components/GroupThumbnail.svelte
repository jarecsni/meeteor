<absoluteLayout backgroundColor="lightgray" margin=4>
    <image 
        src={thumbnail}
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
        {name}
    </label>
</absoluteLayout>

<script>
	export let name, thumbnail;
</script>
