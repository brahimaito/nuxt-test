<script setup>
const route = useRoute();
const config = useRuntimeConfig();
const { data, refresh, pending } = await useFetch(config.public.wordpressUrl, {
  method: "get",
  query: {
    query: `
      query {
        posts(first: 1) {
          nodes {
            id
            title
            date
            excerpt
            slug
            uri
          }
        }
      }
    `,
  },
  transform(data) {
    return data.data.posts.nodes;
  },
});
</script>

<template>
  <div>
    <TheHeader></TheHeader>
    <PostListStyle1></PostListStyle1>
    <!-- <PostListStyle2></PostListStyle2>
    <PostListStyle3></PostListStyle3>
    <PostView></PostView>  -->

    <div class="grid gap-8 grid-cols-1 lg:grid-cols-3 p-6">
      <Post v-for="post in data" :key="post.uri" :post="post"></Post>
    </div>
    <Footer></Footer>
  </div>
</template>
