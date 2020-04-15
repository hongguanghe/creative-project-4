<template>
  <div class="home">
    <section class="image-gallery">
      <ul class="list-comments">
        <li class="each-comments">
          <div class="image" v-for="item in items" :key="item.id">
            <div class="comment">
              <div class="avatar">
                <img :src="item.path" />
              </div>
              <div class="text-info">
                <h2>{{item.title}}</h2>
                <h5 id="author">Author: {{item.author}}</h5>
                <h5>{{item.description}}</h5>
              </div>
            </div>
          </div>
        </li>
      </ul>

    </section>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios';

export default {
  name: 'Home',
  data() {
    return {
     items: [],
    }
  },
  methods: {
    async getItems() {
      try {
        let response = await axios.get("/api/items");
        this.items = response.data;
        return true;
      } catch (error) {
        // console.log(error);
      }
    },
  },
  created() {
    this.getItems();
  },
}
</script>

<style scoped>
.image h2 {
}

.list-comment{
  list-style: none;
  padding: 0;
  list-style-type: none;
  width:100%;
}

.each-comment{
  display: flex;
  flex-direction: column;
}

.comment{
  display: flex;
  flex-direction: row;
  overflow: visible;
}

#author{
  font-style: italic;
}

/* Masonry */
*,
*:before,
*:after {
  box-sizing: inherit;
}

.image-gallery {
  /* row-gap: 1.5em; */
}

/* .image {
  margin: 0 0 1.5em;
  /* display: inline-block; */
  /* width: 100%;
} */

.image img {
  width: 20%;
}
/* } */


</style>
