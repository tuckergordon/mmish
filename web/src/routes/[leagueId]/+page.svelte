<script lang="ts">
  import { page } from '$app/stores';
  import { StandingsTable } from '$lib/components/StandingsTable.js';

  let { data } = $props();
  const { leagueMetadata, posts, standings } = data;
</script>

<div class="prose mx-auto p-4 pt-12 dark:prose-invert">
  <section>
    {#if $page.data?.leagueAvatar}
      <img
        src="https://sleepercdn.com/avatars/{$page.data.leagueAvatar}"
        class="mx-auto h-64 rounded-full"
        alt={$page.data.leagueMetadata.name} />
    {/if}
    <h1>{leagueMetadata.name}</h1>
  </section>

  <section class="justify-between md:flex">
    <div>
      <h2>Standings</h2>
      <!-- eslint-disable-next-line svelte/no-at-html-tags -->
      {@html StandingsTable(standings)}
    </div>

    <ul class="posts mt-0">
      <h2>Recaps</h2>
      {#each posts as post}
        <li class="post">
          <!-- TODO: don't hard code year -->
          <a href="{$page.url.pathname}/posts/2024/{post.fields.slug}" class="title">
            {post.fields.title}
          </a>
        </li>
      {/each}
    </ul>
  </section>
</div>
