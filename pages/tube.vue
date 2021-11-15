<template>
  <div>
    <!-- 1. The <iframe> (and video player) will replace this <div> tag. 
      このセクションの <div> タグは、IFrame API が動画プレーヤーを配置する、ページ上の位置を識別します。
        プレーヤー オブジェクトのコンストラクタ（動画プレーヤーの読み込みのセクションで説明）は、
        id で <div> タグを識別することで、<iframe> を適切な位置に配置します。
        具体的には、IFrame API によって <div> タグが <iframe> タグに置換されます。
    -->
    <div id="player">
      <!-- <iframe
      width="560"
      height="315"
      src="https://www.youtube.com/embed/ZSZhKoloVfM"
      title="YouTube video player"
      frameborder="0"
      allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
      allowfullscreen
    ></iframe>
    <iframe
      width="560"
      height="315"
      src="https://www.youtube.com/embed/fkRtvzS2AVI"
      title="YouTube video player"
      frameborder="0"
      allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
      allowfullscreen
    ></iframe> -->
    </div>
  </div>
</template>
<script lang="ts">
import { defineComponent, ref } from '@nuxtjs/composition-api'
import 'youtube-player'

export default defineComponent({
  setup() {
    // 2. This code loads the IFrame Player API code asynchronously.
    // このセクションのコードにより IFrame Player API JavaScript コードが読み込まれます。
    // この例では DOM 変更を使って API コードをダウンロードすることで、コードが非同期で取得されるようにします。
    const tag = document.createElement('script')
    tag.src = 'https://www.youtube.com/iframe_api'
    const firstScriptTag = document.getElementsByTagName('script')[0]
    firstScriptTag.parentNode!.insertBefore(tag, firstScriptTag)
    // 3. This function creates an <iframe> (and YouTube player) after the API code downloads.
    //   プレーヤー API コードがダウンロードされると、onYouTubeIframeAPIReady 関数が実行されます。
    // コードのこの部分では、組み込もうとしている動画プレーヤーを表すグローバル変数 player を定義します。
    // 続いて、関数によって動画プレーヤー オブジェクトが作成されます。
    const ytPlayer = ref()
    const onYouTubeIframeAPIReady = () => {
      ytPlayer = new YT.Player('player', {
        height: '360',
        width: '640',
        videoId: 'SNqeL4QPaMo',
        events: {
          onReady: onPlayerReady,
        },
      })
    }
    // 4. The API will call this function when the video player is ready.
    // onReady イベントが起動されると、onPlayerReady 関数が実行されます。
    // この例では、関数は動画プレーヤーの準備ができると再生を開始することを指示しています。
    //   const stopVideo = () => {
    //     player.stopVideo()
    //   }
    const onPlayerReady = () => {}
    return {
      // stopVideo,
    }
  },
})
</script>
