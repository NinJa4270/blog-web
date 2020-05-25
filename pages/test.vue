<template>
  <div>
    <ul>
      <li>
        <span>&gt;</span>
        <nuxt-link class="to-Page" to="/" data-text="Home">Home</nuxt-link>
      </li>
      <li>
        <span>&gt;</span>
        <nuxt-link class="to-Page" to="/" data-text="My Articles">My Articles</nuxt-link>
      </li>
      <li>
        <span>&gt;</span>
        <nuxt-link class="to-Page" to="/" data-text="My Projects">My Projects</nuxt-link>
      </li>
      <li>
        <span>&gt;</span>
        <nuxt-link class="to-Page" to="/" data-text="Ohters">Ohters</nuxt-link>
      </li>
      <li>
        <span>&gt;</span>
        <nuxt-link class="to-Page" to="/" data-text="Contact Me">Contact Me</nuxt-link>
      </li>
    </ul>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
}
body {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  background-color: #1c234a;
}
li {
  list-style: none;
  margin: 0 20px;
  font-size: 4em;
}
span{
    position: relative;
    top: -2px;
    left: -10px;
    color: transparent;
}
li:hover span{
    color: #ef0448;
}
.to-Page {
  position: relative;
  color: rgba(255, 255, 255, 0.1);
  text-decoration: none;
  font-weight: 700;
}

.to-Page:before {
  content: attr(data-text);
  position: absolute;
  top: 0;
  overflow-y: hidden;
  color: #1bfaad;
  white-space: nowrap;
  overflow: hidden;
}

ul:hover li .to-Page:before {
  animation: animate 0.5s steps(11) forwards;
}
@keyframes animate {
  0% {
    width: 317.656px;
  }
  100% {
    width: 0px;
  }
}

ul li:hover .to-Page:before {
  animation: animate2 2s steps(11) forwards;
}
@keyframes animate2 {
  0% {
    width: 0;
  }
  100% {
    width: 317.656px;
  }
}
</style>