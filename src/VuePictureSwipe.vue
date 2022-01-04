<template>
  <div>
    <div class="my-gallery" itemscope itemtype="http://schema.org/ImageGallery">
      <figure
        v-for="(item, index) in items"
        v-show="index === 0 || !singleThumbnail"
        :key="index"
        class="wrapperA"
        itemprop="associatedMedia"
        itemscope
        itemtype="http://schema.org/ImageObject"
        :src="item.src"
      >
        <figcaption itemprop="caption description">
          <v-runtime-template
            v-if="item.figcaption"
            :template="item.figcaption"
          ></v-runtime-template>
        </figcaption>
        <a
          v-show="nbThumbnailsDisplayed === -1 || index < nbThumbnailsDisplayed"
          :href="item.src"
          itemprop="contentUrl"
          :data-size="`${item.w}x${item.h}`"
          :title="item.title"
        >
          <img
            :src="item.thumbnail"
            :alt="item.alt"
            itemprop="thumbnail"
            style="height:120px;width:120px;"
            @error="onImageError"
          />
        </a>
        <render-html
          v-if="item.htmlAfterThumbnail"
          :template="item.htmlAfterThumbnail"
        />
      </figure>
    </div>

    <photo-swipe-component
      v-if="defaultStructure"
      :options="options"
    ></photo-swipe-component>
  </div>
</template>

<script>
import PhotoSwipeComponent from "./PhotoSwipeComponent.vue";
import RenderHtml from "./RenderHtml.vue";
import VRuntimeTemplate from "vue3-runtime-template";
export default {
  components: { PhotoSwipeComponent, RenderHtml, VRuntimeTemplate },
  props: {
    items: {
      default: [
        {
          src: "http://via.placeholder.com/600x400",
          thumbnail: "http://via.placeholder.com/64x64",
          w: 0,
          h: 0,
          alt: "some numbers on a grey background",
          figcaption: "ทดสอบ",
        },
        {
          src: "http://via.placeholder.com/1200x900",
          thumbnail: "http://via.placeholder.com/64x64",
          w: 0,
          h: 0,
          figcaption: "<a href='#' style='color: red;' @click='test1()'>X</a>",
        },
      ],
      type: Array,
    },
    options: {
      default: () => ({}),
      type: Object,
    },
    singleThumbnail: {
      type: Boolean,
      default: false,
    },
    nbThumbnailsDisplayed: {
      default: -1,
      type: Number,
    },
    defaultStructure: {
      type: Boolean,
      default: true,
    },
  },
  setup() {
    function onImageError(event) {
      event.target.src = require("@/src/imgnotfound.jpg");
    }
    return {
      onImageError,
    };
  },
};
</script>
<style scoped>
.gallery-thumbnail {
  display: inline;
  margin: 5px;
}

.my-gallery {
  width: 100%;
  float: left;
}
.my-gallery img {
  width: 100%;
  height: auto;
}
.my-gallery figure {
  display: block;
  float: left;
  margin: 0 5px 5px 0;
  width: 150px;
}
.my-gallery figcaption {
  /*display: none;*/
}

.wrapperA {
  width: 400px;
  height: 200px;
  overflow: hidden;
  background-size: cover;
  background-position: center center;
}
</style>
