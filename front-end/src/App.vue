<template>
<div id="app">
  <div class="header">
    <router-link to="/">
      <div class="menu">
        <nav class="navbar navbar-expand-lg navbar-light">
          <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarText" aria-controls="navbarText" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
          </button>
          <div class="collapse navbar-collapse" id="navbarText">
            <ul class="navbar-nav">
              <li class="nav-item">
                <div class="text-link"><router-link to="/">Browse Books</router-link></div>
              </li>
              <li class="nav-item">
                <div class="navbar-brand text-link"><router-link to="/">Books Database</router-link></div>
              </li>
              <li class="nav-item">
                <div class="text-link"><router-link to="/admin">Manage Books</router-link></div>
              </li>
            </ul>
          </div>
        </nav>
      </div>
    </router-link>
    <!-- <div class="title">
      <h1>Museum of Ordinary Objects</h1>
    </div> -->
  </div>
  <div class="content">
    <router-view />
  </div>
  <div class="footer">
    <p><a href="https://github.com/hongguanghe/creative-project-4" target="_blank">Find me on Github</a></p>
  </div>
</div>
</template>

<style>
html {
  box-sizing: border-box;
}

a:hover{
  color:black;
  text-decoration: none;
}

body {
  font-family: 'Montserrat', sans-serif;
  font-size: 16px;
  background: #fff;
  padding: 0px;
  margin: 0px;
}

/* Header */
.header {
  display: flex;
  padding: 10px 100px 10px 100px;
  color: #1C454F;
  justify-content: center;
  border-bottom: 1px solid #c2c2c2;

}

.title {
  margin-top: 5px;
}

.title h1 {
  font-size: 30px;
}

.content {
  padding: 40px 100px;
  min-height: 500px;
}

/* Footer */
.footer {
  height: 50px;
  padding: 20px 100px 0px 100px;
  background: #e3e3e3;
  font-size: 12px;
  text-align: center;
}

.footer a {
  color: #000;
}

h1 {
  font-size: 20px;
}

h2 {
  font-size: 14px;
}

.homepage_banner{
  background-size:cover;
  width: 100%;
  margin-left: 0;
  margin-right: 0;
  background-blend-mode: lighten;
  text-align: center;
  max-width: 100%
}
.container{
  max-width: 100%;
  max-height: 100%;
  padding-left: 0px;
  padding-right: 0px;
}

.main-non-home{
  width:90%;
  margin: auto;
}

.navbar-nav{
  display: flex;
  align-items: center;
}

.menu{
  display: flex;
  justify-content: center;
}
.navbar-brand{
  font-family: 'Dancing Script', cursive;
  font-size: 45px;
  font-style: italic;
  font-weight: bold;
  justify-content: center;
  margin: auto 40px;
}

.navbar .navbar-light{
  display: flex;
  align-items: first baseline;
  justify-content: center;
}

.nav-item{
  text-align: center;
}

.section-title-left{
  font-family: 'Raleway', sans-serif;
  padding-top: 30px;
  padding-bottom: 30px;
  text-align: left;
}

.expiration-date{
  display: flex;
  flex-direction: column;
  width: 100%;
}

.col-4{
}

#expiration{
  display: flex;
  padding-left: 0;

}

#checkout-card{
  margin-top:30px;
  text-align: center;
}

.new-row{
  display: flex;
  flex-direction: row;
}

#h1word{
  padding-bottom: 30px;
}

.nav {
  background-color: rgb(255, 255, 255);
  margin: auto;
  padding.top: 1rem;
  padding-bottom: 1rem;
  padding-left: 0rem;
  padding-right: 0rem;
}

.card p,h5{
  text-align: center;
}

.footer h5{
  text-align: left;
}

#shadow-history{
  float: right;
  margin: 0px 20px;
}

#hisoty-page-pic{
  width: 80%;
}

.section-title{
  font-family: 'Raleway', sans-serif;
  margin: auto;
  padding-top: 30px;
  padding-bottom: 30px;
  text-align: center;
}

.section-title-section{
  font-family: 'Raleway', sans-serif;
  margin: auto;
  padding-bottom: 30px;
  text-align: center;
}


.fruits-selections{
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding-bottom: 30px;
  background-color: #F4F4F4;
}

.card-collection{
  display: flex;
  justify-content: space-between;
}

.col-md-8{
  justify-content: space-between;
  margin-left: 0;
  margin-bottom: 0;
  display: flex;
}

.abcd{
  display: flex;
  justify-content: space-between;
}

.card-body footer{
  text-align: center;
}

.Links ul{
  list-style-type: square;
}

a{
  color:black;
  text-decoration: none;
}

.section-collection{
  display: flex;
  justify-content: space-between;
  padding: 30px 30px;
  flex-wrap: wrap;

}

.row{
  display: flex;
  flex-wrap: wrap;
  margin-bottom: 25px;
}

.col .col-sm-3 .col-sm-4{
  height: 100%;
  margin-left: 25px;
  margin-right: 25px;
}


.col:img{
  width:100%;
  height: 100%;
  margin-top: 15px;
}

.two-side-content{
  display: flex;
  height: 420px;
  justify-content: center;
}

.tickets-content{
  display: flex;
  justify-content:space-between;
  flex-wrap: wrap;

}
.left{
  display: flex;
  width: 30%;
  margin: 50px 50px 0px 0px;
  flex-direction: column;
  justify-content: center;
  text-align: center;
}

.section-title-side{
  margin-left: 30px;
  margin-bottom: 30px;
  text-align: center;
}
.price-number{
  margin-left: 30px;
  margin-bottom: 30px;
  text-align: center;
}
.price-des{
  margin-left: 30px;
  margin-bottom: 30px;
}

.middle{
  margin: 50px 50px;
}

.right{
  max-width: 70%;
  overflow: hidden;
}

.footer-section{
  flex-grow: 0;
}

.footer{
  background-color: #F4F4F4;
}

#history-page-text{
  font-size: 20px;
  line-height: 200%;
  text-indent: 10%;
}

#fruit-page{
  background-color: white;
}

#mail-button{
  height: auto;
  margin-top: 20px;
}

.seventy-side{
  display: flex;
  flex-direction: column;
}
form{
  margin-bottom: 30px;
}

.thirty-side{
}

.footer-title{
  margin-bottom: 20px;
}
.nav-brand{
  display:flex;
  justify-content: center;
  align-items: baseline;
}

.col-info{
  display: flex;
  justify-content: space-around;
}

.card-text{
  /* border-top: 1px solid #2C2C2C; */
}
.row{
  display: flex;
  flex-wrap: wrap;
  margin-bottom: 25px;
}
.text{
  display: flex;
  flex-direction: row;
}
</style>
