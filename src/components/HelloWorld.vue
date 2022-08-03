<template>
  <div class="app">
    <div class="main">
      <div class="title">
        <div class="flex">
          <img src="../SVG/chat.png" alt="" />
          <h1>Chat room</h1>
        </div>
        <h4>Choose a Chat Room</h4>
      </div>
      <div class="grid">
        <div
          class="chat-room"
          v-for="content in contents"
          :key="content"
          @click="() => showChat(content)"
        >
          <div class="content">
            <img :src="content.image" alt="" />
            <p>{{ content.name }}</p>
            <img :src="content.image" alt="" />
          </div>
        </div>
      </div>
    </div>

    <div class="chat-page" v-show="current == true">
      <div class="chat-box">
        <div class="close">
          <button type="button" class="close" @click="closePopUp">x</button>
        </div>
        <div class="room-title">
          <div class="flex">
            <img :src="roomImg" alt="" />
            <h1>{{ roomTitle }}</h1>
            <img :src="roomImg" alt="" />
          </div>

          <div class="flex-p">
            <p><span> ==></span> Back to all rooms</p>
          </div>
          <ul class="chat-text">
            <p class="text" v-for="chat in chats" :key="chat">
              {{ chat }}
            </p>
          </ul>
          <div class="flex">
            <div v-show="!isEditing">
              <input type="text" v-model="text" />
            </div>
            <button @click="newChats" class="button">Send</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// import ChatRoom from './ChatRoom.vue';

export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  components: {
    // ChatRoom
  },
  data() {
    return {
      current: false,
      isEditing: false,
      roomTitle: [],
      roomImg: [],
      text: "",
      chats: [],
      contents: [
        {
          name: "Dog",
          image: [require("../SVG/Dog.png")],
        },
        {
          name: "Food",
          image: [require("../SVG/burger.png")],
        },

        {
          name: "General",
          image: [require("../SVG/chat.png")],
        },
        {
          name: "News",
          image: [require("../SVG/speaker.png")],
        },
        {
          name: "Music",
          image: [require("../SVG/piano.png")],
        },
        {
          name: "Sport",
          image: [require("../SVG/sport.png")],
        },
      ],
    };
  },
  methods: {
    showChat(content) {
        this.current = true;
        this.roomImg = content.image;
        this.roomTitle = content.name;
        this.loadChat();
    },
    closePopUp() {
      this.current = false;
    },

    newChats() {
      this.chats.push(this.text);
      this.text = "";
      this.saveToLocalStorage();
    },
    saveToLocalStorage() {
      localStorage.setItem(
        this.roomTitle.toLowerCase(),
        JSON.stringify(this.chats)
      );
    },
    loadChat() {
        console.log(this.roomTitle);
        const storedData = JSON.parse(localStorage.getItem(this.roomTitle.toLowerCase()));
        if(storedData){
          this.chats = storedData;
        }else{
          this.chats = [];
        }
    
    },
  },
  
};
</script>

<style>
.app {
  display: flex;
  align-items: center;
  justify-content: center;

}

.main {
  background: #222;
  color: antiquewhite;
  align-items: center;
  justify-items: center;
  padding-bottom: 40px;
}
h1 {
  color: antiquewhite;
}
.lar {
  border-radius: 50%;
  color: #fff;
}
.flex {
  display: flex;
  align-items: center;
  justify-content: center;
  padding-bottom: 40px;
  padding-top: 40px;
}

.grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-column: 20px;
  grid-gap: 10px;
  margin: 20px 30px;
}

.chat-room {
  background: #000;
  border: 1px solid #888;
  width: 190px;
  height: 70px;
  border-radius: 3px;
  transition: all 0.3s;
}
.chat-room:hover {
  background: antiquewhite;
  color: #222;
}
.content {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 60px;
}
img {
  width: 20px;
  border-radius: 50px;
  margin: 0px 5px;
}

/* chat-room */
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
.title {
  padding-bottom: 20px;
  padding-left: 20px;
  padding-right: 20px;
  border-bottom: 1px solid #000;
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
.room-title {
  padding-bottom: 20px;
  padding-left: 20px;
  padding-right: 20px;
}
.flex-p {
  /* border-bottom: 1px solid #222; */
  font-size: 14px;
  padding-bottom: 10px;
  color: #dedede;
}
.title h4 {
  font-size: 16px;
}
.chat-box {
  border: 2px solid;
  background-color: #000;
}
.container {
  border: ;
  background-color: #222;
  color: #dedede;
  border-radius: 5px;
  width: 16em;
  padding-right: 40px;
  padding-top: 10px;
  padding-bottom: 10px;
  margin: 10px 0;
}
.container p {
  /* margin: 0px -40px; */
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
.text {
  background: #222;
  color: #dedede;
  font-weight: 600;
  transition: all 0.5s;
  animation: ease-in;
  width: 14em;
  padding-left: 5px;
  /* padding-right: 5px;
  border-radius: 5px; */
}
.chat-text {
  margin-top: 10px;
  padding-left: 5px;
  padding-right: 5px;
}
.chat-text p {
  margin: 10px 0px;
  padding-top: 10px;
  padding-bottom: 10px;
  padding-left: 5px;
  padding-right: 5px;
}
.ta {
}

input {
  width: 100%;
  height: 30px;
  font-size: 18px;
  border-radius: 10px;
  background: #222;
  color: #dedede;
  padding-left: 10px;
}
input:hover {
  border: none;
  outline: none;
}
input:focus {
  border: none;
  outline: none;
}
button {
  padding: 7px 10px;
  background: #407fff;
  border-radius: 5px;
  margin: 0px 10px;
}
</style>
