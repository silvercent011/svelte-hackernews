<script>
  let link;
  $: link = window.location.pathname;

  const routes = [
    { path: "/", title: "New Stories" },
    { path: "/topstories", title: "Top Stories" },
    { path: "/beststories", title: "Best Stories" },
  ];
</script>

<div
  class="fixed bottom-0 left-0 w-full justify-center items-center bg-white p-5 flex gap-5"
>
  {#each routes as route}
    <a class:text-orange-700={link === route.path} href={route.path}
      >{route.title}</a
    >
  {/each}
</div>
