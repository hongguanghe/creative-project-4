<template>
<div class="allContent">
  <h1>Add and Manage Books</h1>
  <div class="info">
    <div class="first">
      <div class="heading">
        <div class="circle">1</div>
        <h2>Add a Book</h2>
      </div>
      <div class="add">
        <div class="form">
          <input v-model="title" placeholder="Title">
          <p></p>
          <input v-model="author" placeholder="Author">
          <p></p>
          <textarea v-model="description" name="name" rows="4" cols="40" placeholder="Enter Description"></textarea>
          <p></p>
          <input type="file" name="photo" @change="fileChanged">
          <button @click="upload" id="submit-button">Submit</button>
        </div>
        <div class="upload" v-if="addItem">
          <h2>{{addItem.title}}</h2>
          <h5>{{addItem.description}}</h5>
          <img :src="addItem.path" />
        </div>
      </div>
    </div>
    <div class="second">
      <div class="heading">
      <div class="circle">2</div>
      <h2>Edit/Delete a Book</h2>
      </div>
      <div class="edit">
        <div class="form">
          <input v-model="findTitle" placeholder="Search by Name" id="searchBox">
          <div class="suggestions" v-if="suggestions.length > 0">
            <div class="suggestion" v-for="s in suggestions" :key="s.id" @click="selectItem(s)">{{s.title}}
            </div>
          </div>
        </div>
        <div class="edit-elements" v-if="findItem">
          <div class="col1">
            <input v-model="findItem.title" placeholder="Edited Name">
            <p></p>
            <input v-model="findItem.author" placeholder="Edited Author">
            <p></p>
            <textarea name="name" rows="4" cols="40" placeholder="Edited Description" v-model="findItem.description"></textarea>
            <div class="col2">
              <img :src="findItem.path" id="picInfo"/>
            </div>
            <div class="actions" v-if="findItem">
              <button @click="editItem(findItem)" id="editButton">Edit</button>
              <button @click="deleteItem(findItem)">Delete</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>



</template>

<script>
import axios from 'axios';

export default {
  name: 'Admin',
  data() {
    return {
      items: [],
      author:"",
      title: "",
      description:"",
      file: null,
      addItem: null,
      selected: false,
      findItem: null,
      findTitle: "",
      findAuthor:"",
      findDescription: "",
      editedTitle:"",
      editedAuthor:"",
    }
  },
  created() {
    this.getItems();
  },
  computed: {
    suggestions() {
      let items = this.items.filter(item => item.title.toLowerCase().startsWith(this.findTitle.toLowerCase()));
      return items.sort((a, b) => a.title > b.title);
    }
  },
  methods: {
    selectItem(item) {
      this.findTitle = "";
      this.findDescription = "";
      this.findItem = item;
      this.findAuthor = "";
    },
    fileChanged(event) {
      this.file = event.target.files[0];
    },
    async upload() {
      try {
        const formData = new FormData();
        formData.append('photo', this.file, this.file.name)
        let r1 = await axios.post('/api/photos', formData);
        let r2 = await axios.post('/api/items', {
          title: this.title,
          author:this.author,
          description: this.description,
          path: r1.data.path
        });
        this.addItem = r2.data;
      } catch (error) {
        return "Error";
      }
    },
    async deleteItem(item) {
      try {
        await axios.delete("/api/items/" + item._id);
        this.findItem = null;
        this.getItems();
        return true;
      } catch (error) {
        return "Error";

      }
    },
    async editItem(item) {
      try {
        await axios.put("/api/items/" + item._id, {
          title: this.findItem.title,
          author: this.findItem.author,
          description: this.findItem.description,
        });
        this.findItem = null;
        this.getItems();
        return true;
      } catch (error) {
        return "Error";

      }
    },
    async getItems() {
      try {
        let response = await axios.get("/api/items");
        this.items = response.data;
        return true;
      } catch (error) {
        return "Error";

      }
    },

  }
}
</script>

<style scoped>
.picInfo{
  height:250px;
  margin-top:10px;
}

.image h2 {
  font-style: italic;
  font-size: 1em;
}

.heading {
  display: flex;
  margin-bottom: 20px;
  margin-top: 20px;
}

.heading h2 {
  margin-top: 8px;
  margin-left: 10px;
}

.add,
.edit {
  display: flex;
}

.circle {
  border-radius: 50%;
  width: 40px;
  height: 40px;
  padding: 8px;
  background:#ffbb00;
  color: #fff;
  text-align: center
}

/* Form */
input,
textarea,
select,
button {
  font-family: 'Montserrat', sans-serif;
  font-size: 1em;
}

.form {
  margin-right: 50px;
}

/* Uploaded images */
.upload h2 {
  margin: 0px;
}

.upload img {
  max-width: 300px;
}

.itemLists{
  display: flex;
  flex-direction: row;
}

.col1{
  margin-right: 20px;
}

.col2 img{
  max-width: 300px;
}

.edit-elements{
  display: flex;
  flex-direction: row;
  justify-content: space-space-between;
}

.actions{
  margin-top: 30px;
}

#editButton{
  margin-right: 10px;
}

.info{
  display: flex;
  flex-direction: row;
}

#searchBox{
  margin-bottom: 10px;
}

#submit-button{
  margin-top: 10px;
}

</style>
