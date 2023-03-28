 <router-view v-slot="{ Component }">
    <component :is="Component" @savedText="storeSavedText" :textToDisplay="savedTextSendDown" />
  </router-view>
