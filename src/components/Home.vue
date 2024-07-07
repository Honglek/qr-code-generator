<template>
  <div class="w-full flex flex-col h-screen">
    <main class="w-10/12 mx-auto flex-grow flex items-center justify-center1">
      <div class="w-full">
        <h1 class="text-left text-lg font-bold">QR Code Generator</h1>
        <div class="w-full p-3 border-2 border-gray-200">
          <h2 class="text-base">Enter your text or url</h2>
          <input
            type="search"
            v-model="text"
            class="w-full p-2 mt-2 bg-gray-300 focus:outline-none text-sm rounded-md"
          />
          <img
            :src="qrcode"
            alt="QR Code"
            class="mx-auto min-w-48 min-h-48 max-w-full max-h-full border-2 border-gray-200 my-4"
          />

          <button
            @click="downloadQRCode"
            class="w-full bg-orange-500 text-white p-2"
          >
            Download
          </button>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
import { ref } from "vue";
import { useQRCode } from "@vueuse/integrations/useQRCode";
export default {
  name: "Home",
  setup() {
    const text = ref("https://honglek.vercel.app");
    const qrcode = useQRCode(text);
    const downloadQRCode = () => {
      const link = document.createElement("a");
      link.href = qrcode.value;
      link.download = "qrcode.png";
      link.click();
    };
    return {
      text,
      qrcode,
      downloadQRCode,
    };
  },
};
</script>
