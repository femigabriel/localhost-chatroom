<template>
  <div class="chat-page">
    <div class="chat-box">
      <div class="close">
        <button type="button" class="close" @click="close = true">
          x
        </button>
      </div>
      <div class="roo-title">
        <div class="flex">
          <img src="../SVG/dogsvg.png" alt="" />
          <h1>Dogs</h1>
          <img src="../SVG/dogsvg.png" alt="" />
        </div>
        <div class="flex-p"  @click="close = true">
          <!-- <p><span> ==> </span> Welcome to m</p> -->
        </div>
        <div class="container" v-for="text in texts" :key="text">
          <p class="name">{{ text.chatName }}</p>
          <p class="text">{{ text.message }}</p>
        </div>
        <div class="flex">
          <input class="storage" type="text" v-model="newChats" />
          <button @click="submitChats" class="button">Send</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  // emits: ["submitChats"],
  data() {
    return {
      close: false,
      newChats: "",
      texts: [
        {
          chatName: "Zach Zoe",
          message: "Hey babe",
        },
        {
          chatName: "Peter Zoe",
          message: "Hey Sweet",
        },
        {
          chatName: "Zach Zoe",
          message: "what's up?",
        },
        {
          chatName: "Peter Zoe",
          message: "Going well!, you?",
        },
      ],
    };
  },
  close() {
    // this.$emit("submitChats", this.texts)
    // this.newChats.push(this.texts);
    // this.newChats = this.texts;
    console.log("Hello Testing");
  },
};
</script>

<style>
.chat-page {
  display: flex;
  background: rgba(51, 51, 51, 0.338);
  position: fixed;
  width: 100%;
  height: 100%;
  align-items: center;
  justify-content: center;
  margin-bottom: -200px;
}
.container {
  border: 2px solid #dedede;
  background-color: #f1f1f1;
  border-radius: 5px;
  padding: 10px;
  margin: 10px 0;
}
.close {
  border: none;
  font-size: 30px;
  margin-left: 180px;
  cursor: pointer;
  /* font-weight: bold; */
  color: #a9a9c5;
  background: transparent;
}
.darker {
  border-color: #ccc;
  background-color: #ddd;
}
.container::after {
  content: "";
  clear: both;
  display: table;
}
.time-right {
  float: right;
  color: #aaa;
}

.time-left {
  float: left;
  color: #999;
}
</style>
