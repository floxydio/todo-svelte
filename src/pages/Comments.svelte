<script>
    let dataComments = [];

    fetch("https://jsonplaceholder.typicode.com/comments", {
        method: "GET"
    }).then(response => response.json()).then(data => {
        dataComments = data;
    });
    
</script>

{#each dataComments.slice(0,10) as comment}
    <div class="comment">
        <h3>{comment.name}</h3>
        <p>{comment.body}</p>
    </div>
{/each}


<style></style>