<script lang="ts">
  import PostsListNav from '$lib/components/PostsListNav.svelte';
  import { TableOfContents } from '@skeletonlabs/skeleton';
  import type { Snippet } from 'svelte';

  let { children }: { children?: Snippet } = $props();
</script>

<div class="container mx-auto grid grid-cols-1 pt-6 lg:grid-cols-[200px_minmax(0px,_1fr)_200px]">
  <!-- 100px leaves room for navbar -->
  <aside class="sticky top-[100px] col-span-1 hidden h-screen scroll-mt-[100px] lg:block">
    <div class="p-4 pt-0 font-bold">Recaps</div>
    <PostsListNav />
  </aside>

  <main class="col-span-1 space-y-4 px-8 py-0">
    {@render children?.()}
  </main>

  <aside class="sticky top-[100px] col-span-1 hidden h-screen scroll-mt-[100px] lg:block">
    <TableOfContents>On The Page</TableOfContents>
  </aside>
</div>
