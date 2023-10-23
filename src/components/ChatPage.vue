<template>
    <div v-if="username">
        <div class="chat-container">
            <div class="chat">
                <h2>Чат</h2>
                <div class="text" v-for="message in messages" :key="message.id">
                    {{ message.username }}:{{ message.text }}
                </div>
                <div v-show="emptyMsg" class="empty">
                    Сообщений пока нет
                </div>
            </div>
            <textarea v-model="newMessage" placeholder="Ваше сообщение..." class="big-input"></textarea>
        </div>
        <div class="button-container">
            <button @click="sendMessage" @keyup.enter="sendMessage">Отправить</button>
            <button v-show="deleteBtn" @click="delMessage">Очистить</button>
        </div>
    </div>
    <div v-else class="alert">
        Необходима <router-link :to="{ name: 'Home' }">авторизация</router-link>
    </div>
</template>
  
  
<script>
export default {
    name: 'ChatPage',
    data() {
        return {
            messages: [],
            newMessage: '',
            emptyMsg: true,
            deleteBtn: false,
            username: null,
        };
    },
    methods: {
        sendMessage() {
            if (!this.username) {
                this.username = 'Аноним';
            }

            if (this.newMessage !== '') {
                this.emptyMsg = false;
                console.log('Вы написали', this.newMessage);
                this.messages.push({
                    id: new Date().getTime(),
                    text: this.newMessage,
                    username: this.username,
                });
                this.saveChatRecords();
                this.newMessage = '';
                this.deleteBtn = true;
            } else {
                console.log('Напишите сообщение');
                alert('Нельзя отправить пустое сообщение');
            }
        },
        delMessage() {
            this.messages = [];
            localStorage.removeItem(`messages_${this.username}`);
            console.log('All messages deleted');
            this.emptyMsg = true;
        },
        saveChatRecords() {
            const records = this.messages;
            console.log(records);
            localStorage.setItem(`messages_${this.username}`, JSON.stringify(records));
        },
        loadChatRecords() {
            const records = JSON.parse(localStorage.getItem(`messages_${this.username}`));
            if (records) {
                this.messages = records;
                this.emptyMsg = false;
            }
        },
    },
    created() {
        this.username = localStorage.getItem('username');
        this.loadChatRecords();
    },
};
</script>
  
  
<style scoped>
h2 {
    color: #333;
}

.text {
    margin-bottom: 25px;
}

.chat {
    width: 600px;
    height: auto;
    border: 1px solid #ddd;
    border-radius: 9px;
    color: #aaa;
    font-weight: 300;
    margin: 20px;
    padding: 15px;
    box-shadow: 4px 4px 21px 11px rgba(34, 60, 80, 0.05);
    background-color: #fffafa;
}

.empty {
    margin-bottom: 30px;
    font-style: italic;
}

button {
    margin: 20px;
}

.alert {
    padding: 30px;
    color: #ccc;
}

a {
    color: #8c86fe;
    font-weight: 700;
    ;
}

.big-input {
    width: 90%;
    height: 100px;
    border: 1px solid #ddd;
    background-color: rgb(251, 255, 218);
    padding: 10px;
    border-radius: 9px;
}

.chat-container {
    display: flex;
    flex-direction: column;
    align-items: center;
}

.button-container {
    display: flex;
    justify-content: center;
}
</style>