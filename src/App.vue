<template>
  <div id="nav">
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </div>
  <router-view/>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}

.btnCont {
  margin: 3em auto;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  width: 640px;
  justify-content: center;
  align-items: center;
}

.btn {
  margin: .5em auto;
  width: 10em;
  height: 3em;
  border: 0px;
  border-radius: 15px;
}

.clear {
  background: red;
  color: white;
}

.equal {
  background: rgb(11, 243, 11);
}

.disMain {
  margin: auto;
  width: 540px;
  height: 80px;
  max-height: 80px;
  background: #efefef;
  padding: 2px;
}

div.disMain {
  margin: auto;
  border: none;
  text-align: end;
  font-size: 27px;
  padding: auto;
  display: flex;
  align-items: center;
  justify-content: end;
}

.disP {
  margin: 0px;
}

input {
  margin: auto;
  border: none;
  text-align: end;
  font-size: 27px;
  height: 80px;
  max-height: 80px;
}

</style>
