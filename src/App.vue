<template>
  <div
    class="song"
    v-for="nowplaying in nowplaying_arr"
    :class="nowplaying.status"
  >
    <span class="song-title">
      {{ nowplaying.artist }} - {{ nowplaying.title }}
      <br />
      ({{ nowplaying.duration }})
    </span>
    <a
      class="link"
      :class="nowplaying.status"
      :href="nowplaying.iTunesTrackUrl"
      target="_blank"
    >
      <img :src="nowplaying.imageUrl" :alt="nowplaying.title" />
    </a>
    <div v-if="nowplaying.status == 'playing'" style="color: #009688">
      &#9658; Now playing
    </div>
    <div v-else>
      &#9209;
      {{ handleDate(nowplaying.time) }}
    </div>
  </div>
</template>

<script>
import $ from 'jquery';
export default {
  data() {
    return {
      nowplaying_arr: [],
    };
  },
  methods: {
    startChecking() {
      setInterval(() => {
        console.log('------updating------');
        $.getJSON('onair.json', (data) => {
          this.nowplaying_arr = data.nowplaying;
        });
      }, 2000);
    },
    handleDate(date_str) {
      let locTime = new Date(date_str);
      return locTime.toLocaleTimeString();
    },
  },
  mounted() {
    console.log('mounted');
    this.startChecking();
    this.nowplaying_arr = jsn.nowplaying;
  },
};
let jsn = {
  nowplaying: [
    {
      artist: 'Robbie Williams',
      duration: '00:03:19',
      iTunesTrackUrl:
        'https://itunes.apple.com/gb/album/candy/id565997914?i=565997918&uo=4',
      imageUrl:
        'http://is4.mzstatic.com/image/thumb/Music/v4/90/9d/16/909d16ba-4470-b824-ee3b-41ab25546e81/source/450x450bb.jpg',
      previewUrl: '',
      status: 'playing',
      time: '2022-12-26T17:24:32Z',
      title: 'Candy',
    },
    {
      artist: 'Jamiroquai',
      duration: '00:03:18',
      iTunesTrackUrl:
        'https://itunes.apple.com/gb/album/canned-heat/id217052057?i=217052141&uo=4',
      imageUrl:
        'http://is4.mzstatic.com/image/thumb/Music/v4/7b/84/3d/7b843d96-5b8f-ecbb-f2fd-ce3a4261dc7b/source/450x450bb.jpg',
      previewUrl: '',
      status: 'history',
      time: '2022-12-26T17:21:07Z',
      title: 'Canned Heat',
    },
    {
      artist: 'Justin Bieber',
      duration: '00:03:22',
      iTunesTrackUrl:
        'https://itunes.apple.com/gb/album/what-do-you-mean/id1049359399?i=1049359404&uo=4',
      imageUrl:
        'http://is3.mzstatic.com/image/thumb/Music69/v4/e2/aa/01/e2aa018a-7c57-f15c-c1ff-b8cf979344f5/source/450x450bb.jpg',
      previewUrl: '',
      status: 'history',
      time: '2022-12-26T17:17:43Z',
      title: 'What Do You Mean',
    },
    {
      artist: 'Amy Macdonald',
      duration: '00:03:33',
      iTunesTrackUrl:
        'https://itunes.apple.com/gb/album/mr-rock-roll/id260315342?i=260315344&uo=4',
      imageUrl:
        'http://is3.mzstatic.com/image/thumb/Music/v4/f1/b4/00/f1b400a4-af04-5b9c-f8c4-9293ab0ff554/source/450x450bb.jpg',
      previewUrl: '',
      status: 'history',
      time: '2022-12-26T17:12:02Z',
      title: 'Mr Rock & Roll',
    },
    {
      artist: 'Beyonce',
      duration: '00:04:27',
      iTunesTrackUrl:
        'https://itunes.apple.com/gb/album/love-on-top/id626204707?i=626205216&uo=4',
      imageUrl:
        'http://is1.mzstatic.com/image/thumb/Music/v4/96/b5/28/96b5280d-379c-af56-a0f5-1825b7a411b4/source/450x450bb.jpg',
      previewUrl: '',
      status: 'history',
      time: '2022-12-26T17:07:37Z',
      title: 'Love on Top',
    },
    {
      artist: 'Calvin Harris & Disciples',
      duration: '00:03:28',
      iTunesTrackUrl:
        'https://itunes.apple.com/gb/album/how-deep-is-your-love/id1001677304?i=1001677305&uo=4',
      imageUrl:
        'http://is2.mzstatic.com/image/thumb/Music7/v4/77/03/5d/77035dba-febd-f8db-5641-219ba45881d6/source/450x450bb.jpg',
      previewUrl: '',
      status: 'history',
      time: '2022-12-26T17:04:10Z',
      title: 'How Deep Is Your Love',
    },
    {
      artist: 'Meghan Trainor',
      duration: '00:02:14',
      iTunesTrackUrl:
        'https://music.apple.com/gb/album/made-you-look/1630437323?i=1630437329&uo=4',
      imageUrl:
        'https://is2-ssl.mzstatic.com/image/thumb/Music112/v4/e2/b6/c9/e2b6c962-e585-85c5-841b-64c01aa35834/196589214188.jpg/450x450bb.jpg',
      previewUrl: '',
      status: 'history',
      time: '2022-12-26T17:01:54Z',
      title: 'Made You Look',
    },
    {
      artist: 'Rita Ora',
      duration: '00:03:10',
      iTunesTrackUrl:
        'https://itunes.apple.com/gb/album/let-you-love-me/1436290232?i=1436290337&uo=4',
      imageUrl:
        'https://is2-ssl.mzstatic.com/image/thumb/Music118/v4/97/5a/9a/975a9aaf-d087-2ccf-73c7-f305a698e270/source/450x450bb.jpg',
      previewUrl: '',
      status: 'history',
      time: '2022-12-26T16:58:47Z',
      title: 'Let You Love Me',
    },
    {
      artist: 'The Chainsmokers',
      duration: '00:04:06',
      iTunesTrackUrl:
        'https://music.apple.com/gb/album/something-just-like-this-tokyo-remix/1245878924?i=1245878927&uo=4',
      imageUrl:
        'https://is2-ssl.mzstatic.com/image/thumb/Music127/v4/ed/a6/a8/eda6a8a5-daef-046e-3b33-cc23db06cb26/886446563534.jpg/450x450bb.jpg',
      previewUrl: '',
      status: 'history',
      time: '2022-12-26T16:52:55Z',
      title: 'Something Just Like This (Feat. Coldplay)',
    },
    {
      artist: 'Livin Joy',
      duration: '00:03:35',
      iTunesTrackUrl:
        'https://music.apple.com/gb/album/dont-stop-movin/1361726459?i=1361728000&uo=4',
      imageUrl:
        'https://is4-ssl.mzstatic.com/image/thumb/Music62/v4/fb/59/8b/fb598b2e-3f9c-d656-3b7d-e0ca9a74b539/885012025094.jpg/450x450bb.jpg',
      previewUrl: '',
      status: 'history',
      time: '2022-12-26T16:41:40Z',
      title: "Don't Stop Moving",
    },
    {
      artist: 'Walk the Moon',
      duration: '00:03:16',
      iTunesTrackUrl:
        'https://itunes.apple.com/gb/album/shut-up-and-dance/id915448845?i=915448860&uo=4',
      imageUrl:
        'http://is4.mzstatic.com/image/thumb/Music5/v4/bc/0c/ea/bc0cea20-d0ce-c5b5-a081-d5af3e39af72/source/450x450bb.jpg',
      previewUrl: '',
      status: 'history',
      time: '2022-12-26T16:38:22Z',
      title: 'Shut Up and Dance',
    },
    {
      artist: 'Macklemore',
      duration: '00:03:08',
      iTunesTrackUrl:
        'https://itunes.apple.com/gb/album/cant-hold-us-feat-ray-dalton/id560097651?i=560097694&uo=4',
      imageUrl:
        'http://is4.mzstatic.com/image/thumb/Music/v4/34/7d/75/347d759e-0ac7-ee1c-1cad-a71dd783b838/source/450x450bb.jpg',
      previewUrl: '',
      status: 'history',
      time: '2022-12-26T16:33:23Z',
      title: "Can't Hold Us",
    },
    {
      artist: 'Rihanna',
      duration: '00:03:56',
      iTunesTrackUrl:
        'https://itunes.apple.com/gb/album/only-girl-in-the-world/id458304705?i=458304723&uo=4',
      imageUrl:
        'http://is1.mzstatic.com/image/thumb/Music/v4/d5/6d/8f/d56d8f6e-a797-707e-5475-29ae782bce60/source/450x450bb.jpg',
      previewUrl: '',
      status: 'history',
      time: '2022-12-26T16:29:28Z',
      title: 'Only Girl (In the World)',
    },
    {
      artist: 'Shawn Mendes',
      duration: '00:03:29',
      iTunesTrackUrl:
        'https://itunes.apple.com/gb/album/in-my-blood/1359906692?i=1359907549&uo=4',
      imageUrl:
        'http://is2.mzstatic.com/image/thumb/Music128/v4/6c/f6/37/6cf637f4-cb77-660e-a94d-642304f22611/source/450x450bb.jpg',
      previewUrl: '',
      status: 'history',
      time: '2022-12-26T16:26:01Z',
      title: 'In My Blood',
    },
    {
      artist: 'Tlc',
      duration: '00:03:39',
      iTunesTrackUrl:
        'https://itunes.apple.com/gb/album/no-scrubs/id298575243?i=298575248&uo=4',
      imageUrl:
        'http://is5.mzstatic.com/image/thumb/Music1/v4/89/63/42/89634250-eed4-a474-cf18-8b55cab575da/source/450x450bb.jpg',
      previewUrl: '',
      status: 'history',
      time: '2022-12-26T16:22:05Z',
      title: 'No Scrubs',
    },
    {
      artist: 'Eric Prydz',
      duration: '00:02:40',
      iTunesTrackUrl:
        'https://itunes.apple.com/gb/album/pjanoo-radio-edit/id1216951593?i=1216951600&uo=4',
      imageUrl:
        'http://is2.mzstatic.com/image/thumb/Music82/v4/76/96/b6/7696b6d5-b216-caa9-3414-f9fbbfbb10cf/source/450x450bb.jpg',
      previewUrl: '',
      status: 'history',
      time: '2022-12-26T15:51:59Z',
      title: 'Pjanoo',
    },
  ],
};
</script>
