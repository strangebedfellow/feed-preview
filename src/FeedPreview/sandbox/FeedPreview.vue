<template>
  <div>
    <feed-preview :url="url"></feed-preview>
  </div>
</template>
<script>
import FeedPreview from "./../src/FeedPreview";

export default {
  name: "FeedPreviewSandbox",
  components: { FeedPreview },
  data() {
    return {
      url: "https://www.gamespot.com/feeds/mashup/"
    }
  },
};
</script>
<style lang="scss" scoped></style>
