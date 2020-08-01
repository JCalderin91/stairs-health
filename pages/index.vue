<template>
  <div>
    <hero />
    <categories />
    <clinics />
    <features />
    <parallax />
  </div>
</template>

<script>
import { createClient } from "~/plugins/contentful.js";

import Hero from "~/components/views/home/Hero";
import Categories from "~/components/views/home/Categories";
import Clinics from "~/components/views/home/Clinics";
import Features from "~/components/views/home/Features";
import Parallax from "~/components/views/home/Parallax";

const client = createClient();

export default {
  components: {
    Hero,
    Categories,
    Clinics,
    Features,
    Parallax,
  },
  asyncData() {
    return Promise.all([
      // fetch the owner of the blog
      client.getEntries(),
      // fetch all blog posts sorted by creation date
      client.getEntries({
        content_type: "category",
      }),
    ])
      .then(([entries, posts]) => {
        // return data that should be available
        // in the template
        console.log("entries", entries);
        console.log("post", posts);
        return {
          posts,
          entries,
        };
      })
      .catch(console.error);
  },
};
</script>

