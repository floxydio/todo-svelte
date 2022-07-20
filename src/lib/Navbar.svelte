<script>
    	import { Router, Link, Route } from "svelte-navigator";

    let menuData = [{
        title: "Home",
        url: "/"
    },{
        title: "Comments",
        url: "comment"
    }, {
        title: "Posts",
        url: "post"
    }];

</script>

<div class="nav">
    <h2>TODO Blog By IO</h2>
    <div class="menu-right">
        {#each menuData as menu}
            <span><Link to={menu.url}>{menu.title}</Link></span>
        {/each}
    </div>
</div>

<style>
    .nav {
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
    .menu-right span {
        cursor: pointer;
        margin-left: 20px ;
    }

</style>