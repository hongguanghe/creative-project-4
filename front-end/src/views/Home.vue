<template>
  <div class="home">
    <h1 id="pageTitle">Books Catalog</h1>
    <section class="image-gallery">
      <ul class="list-comments">
        <li class="each-comments" v-for="item in items" :key="item.id">
          <div class="image">
            <div class="comment">
              <div class="avatar">
                <img :src="item.path" id="pic"/>
              </div>
              <div class="text-info">
                <p id="title">{{item.title}}</p>
                <p id="author">by {{item.author}}</p>
                <p id="description">{{item.description}}</p>
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

#pageTitle{
  font-size: 30px;
  font-weight: bold;
  text-align: center;
  margin-bottom: 40px;
}

.list-comments{
  list-style: none;
  padding: 0;
  list-style-type: none;
  width:100%;
}

.each-comments{
  display: flex;
  flex-direction: column;
  border-top: 1px solid #c2c2c2;
  padding: 30px;
}

.comment{
  display: flex;
  flex-direction: row;
}

#title{
  font-weight: bold;
  font-size: 25px;
  color:black;

}

#author{
  font-style: italic;
  font-size: 15px;
  color:black;

}

#description{
  color:black;
  font-size: 20px;
}

/* Masonry */
/* *,
*:before,
*:after {
  box-sizing: inherit;
} */

.image-gallery {
  /* row-gap: 1.5em; */
}

/* .image {
  margin: 0 0 1.5em;
  /* display: inline-block; */
  /* width: 100%;
} */


#pic{
  height: 250px;
}

.text-info{
  margin-left: 30px;
}

</style>
