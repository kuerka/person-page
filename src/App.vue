<template>
  <div class="background"></div>
  <div class="container">
    <div class="title"></div>
    <div class="menu">
      <a v-for="{ name, link } of menus" class="item" :href="goto(link)" :key="link">
        {{ name }}
      </a>
    </div>
  </div>
</template>

<script setup lang="ts">
type MenuItem = {
  name: string;
  link: string;
};

const menus: MenuItem[] = [
  { name: "Code Server", link: ":3031" },
  { name: "文件管理", link: "/file_mange" },
  { name: "聊天室", link: ":3033" },
];

const goto = (link: string) => {
  return `http://${window.location.hostname}${link}`;
};
</script>

<style scoped lang="less">
.background {
  z-index: -99;
  position: fixed;
  width: 100dvw;
  height: 100dvh;
  background: url("/picture/夜解きの魔女.jpg");
  background-repeat: no-repeat;
  background-size: cover;
}

.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 80dvw;
  height: 80dvh;
  margin: auto;
  border-radius: 2rem;
  backdrop-filter: blur(3px);
  box-shadow: 0px 0px 10px grey;

  .title {
    font-size: 3rem;
    color: white;
    text-shadow: 0px 0px 10px black;
  }

  .menu {
    display: flex;
    flex-direction: column;
    align-items: center;

    .item {
      width: 10rem;
      margin: 1rem;
      padding: 0.5rem;
      border-radius: 5px;
      color: white;
      text-shadow: 0px 0px 5px black;
      text-align: center;
      text-decoration: none;
      background: rgba(255, 255, 255, 0.3);
      cursor: pointer;

      &:hover {
        transition: all 0.25s;
        background: rgba(255, 255, 255, 0.4);
      }
    }

    /* justify-content: center; */
  }
}
</style>
