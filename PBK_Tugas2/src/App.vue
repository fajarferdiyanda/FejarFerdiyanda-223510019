<template>
  <div class="container mx-auto p-4">
    <h1 class="text-3xl font-bold mb-4">Message Board</h1>
    <div class="mb-4">
      <input v-model="name" type="text" placeholder="Your Name" class="border border-gray-300 p-2 rounded-md w-full">
    </div>
    <div class="mb-4">
      <textarea v-model="message" placeholder="Your Message" class="border border-gray-300 p-2 rounded-md w-full h-32 resize-none"></textarea>
    </div>
    <button @click="postMessage" class="button-post">Post Message</button>
    <div v-if="messages.length" class="mt-8">
      <h2 class="text-xl font-bold mb-2">Messages</h2>
      <div v-for="(msg, index) in messages" :key="index" class="message-box">
        <p class="font-bold text-black">{{ msg.name }}</p>
        <p class="text-black">{{ msg.message }}</p>
        <button @click="deleteMessage(index)" class="button-delete">Delete</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: '',
      message: '',
      messages: []
    };
  },
  methods: {
    postMessage() {
      if (this.name && this.message) {
        this.messages.unshift({
          name: this.name,
          message: this.message
        });
        this.name = '';
        this.message = '';
      } else {
        alert('Please fill in both fields.');
      }
    },
    deleteMessage(index) {
      this.messages.splice(index, 1);
    }
  }
};
</script>

<style>


h1{
  color: black;
  font-family: 'broadway';
  font-size: 50px;
  position: absolute;
  top: 0;
  left: 50%;
  transform: translate(-50%, 0);
}

p{
  color: black;
  font-family: 'Times New Roman', Times, serif;
}



body {
    background-color: rgb(0, 255, 204);
    
}


/* Style untuk tombol "Post Message" */
.button-post {
  transition: background-color 0.3s ease;
  background-color: #4299e1;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  
  
  
}

.button-post:hover {
  background-color: #3182ce;
  
  
}

/* Style untuk tombol "Delete" */
.button-delete {
  transition: color 0.3s ease;
  color: #e53e3e;
  background-color: transparent;
  border: none;
  padding: 4px 8px;
  border-radius: 4px;
  cursor: pointer;
}

.button-delete:hover {
  color: #c53030;
}

/* Style untuk kotak pesan */
.message-box {
  transition: box-shadow 0.3s ease;
  background-color: #f7fafc;
  padding: 12px;
  border-radius: 4px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.message-box:hover {
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1), 0 1px 3px rgba(0, 0, 0, 0.08);
}

/* Style untuk teks pada pesan */
textarea {
  color: black; /* Mengatur warna teks yang diinputkan menjadi hitam */
  
  
}
</style>
