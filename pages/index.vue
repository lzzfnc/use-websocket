<template>
    <div class="container">
        data: {{ data }} <br />
        status: {{ status }} <br />

        <input v-model="message" type="text" />
        <button @click="send(message)">Send</button> <br />

        <button @click="close()">Close</button>
    </div>
</template>
<script>
import { useWebSocket } from "@vueuse/core";
export default {
    setup() {
        const { status, data, send, close } = useWebSocket(
            "wss://echo.websocket.org"
        );

        return {
            status,
            data,
            send,
            close,
        };
    },
    data() {
        return {
            message: "",
        };
    },
};
</script>
<style >
.container {
    margin: 50px;
}

.container > * {
    margin: 10px auto;
}
</style>
