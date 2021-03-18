<template>
    <footer>
        <p>Made by Caleb Hunt</p>
        <a href="https://github.com/BYU-CS-260-Winter-2021/lab-3b-grocery-store-Kaychub"><img src="/images/GitHub-Mark-32px.png" title="Github Repo for this project" ></a>
  </footer>
</template>

<script>
export default {
    name: 'Footer',
}
</script>

<style scoped>
    footer {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    align-items: center;
    background-color: #ddd;
    color: #000;

    max-height: 40px;
    
    padding-top: 10px;
    
    position: fixed;
    bottom: 0;
    left: 0;
    width: 100%;
}
</style>