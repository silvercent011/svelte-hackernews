<script>
  import { onMount } from "svelte";

  export let postid;

  let post = {
    data: null,
    loading: false,
  };

  onMount(async () => {
    post.loading = true;
    const response = await fetch(
      `https://hacker-news.firebaseio.com/v0/item/${postid}.json`
    );
    const json = await response.json();
    post.data = json;
    post.loading = false;
  });
</script>

{#if post.data !== null && post.loading === false}
  <a href={post.data.url} target="_blank" rel="noreferrer">
    <div
      class="bg-orange-100 p-5 rounded-lg hover:bg-orange-600 hover:text-white transition-all cursor-pointer group"
    >
      <h1 class="font-bold text-2xl">{post.data.title}</h1>
      <p>
        by <span class="text-orange-600 group-hover:text-orange-100">
          {post.data.by}
        </span>
      </p>
      {new Date(post.data.time * 1000).toLocaleString()}
    </div>
  </a>
{:else}
  <p>Loading...</p>
{/if}
