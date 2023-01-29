<script>
  import { onMount } from "svelte";
  import Header from "../components/Header.svelte";
  import Post from "../components/Post.svelte";

  let posts = {
    data: [],
    loading: false,
  };

  onMount(async () => {
    posts.loading = true;
    const response = await fetch(
      "https://hacker-news.firebaseio.com/v0/beststories.json"
    );
    const json = await response.json();
    posts.data = json;
    posts.loading = false;
  });
</script>

<Header title="Best Stories" />
<div class="p-5">
  {#if posts.loading === true}
    <h1>Loading...</h1>
  {:else if posts.data.length > 0}
    <div class="flex flex-col gap-2">
      {#each posts.data as postid}
        <Post {postid} />
      {/each}
    </div>
  {/if}
</div>
