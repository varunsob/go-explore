<template>
  <div class="card">
    <img class="bg-img" :src="imgUrl" />
    <div class="category-label">
        {{venue.venue.categories[0].name}}
    </div>
    <div class="venue-details">
      <label class="venue-title">{{venue.venue.name}}</label><br/>
      <label class="venue-distance">{{(venue.venue.location.distance / 1000).toFixed(2) }} Kms</label>
    </div>
  </div>
</template>

<script>
import Vue from 'vue';
import VueResource from 'vue-resource';
Vue.use(VueResource);

export default {
  name: 'Card',

  props: {
    venue: Object,
    msg: String
  },

  data() {
    return {
      imgUrl: null,
    }
  },

  created() {
    console.log("fetch images");
    this.fetchVenueImage();
  },

  methods: {
    fetchVenueImage() {
      Vue.http.get('https://api.foursquare.com/v2/venues/'+ this.venue.venue.id +'/photos?client_id=Z1HSHTJQLY4XT3YXGXJJNPWUFPJHPZDUJAE3LMFKXUPS0UJ3&client_secret=LYSNFZR5UBCE433BFKAHQXULOHRQYP1LEYQWBX5QHF5235ED&v=20190714')
      .then(response => {
        this.imgUrl = response.data.response.photos.items[0].prefix + "512" + response.data.response.photos.items[0].suffix;
      })
      .catch(error => {
        // TODO (varunsobti): Replace external path with CDN location.
        this.imgUrl = "https://b2303ztyja-flywheel.netdna-ssl.com/wp-content/uploads/2016/09/Restaurant-Placeholder-001.jpg";
      });
    }
  }
}   
</script>

<style scoped>
.bg-img {
  background: #efefef;
  height: 150px;
  object-fit: cover;
  opacity: 0.8;
  width: 100%;
  
}
.card {
  display: inline-block;
  height: 150px;
  margin: 5px 0;
  position: relative;
  width: 90%;
}
.category-label {
  background-color: #fff;
  font-size: 10px;
  font-weight: 600;
  padding: 4px 8px;
  margin-top: 5px;
  position: absolute;
  top: 0;
}
.title {
  font-size: 14px;
  top: 0;
}
.venue-details {
  /* background-color: #efefef; */
  background: linear-gradient(45deg, #fff 0%, transparent 100%);
  bottom: 0;
  height: 35px;
  position: absolute;
  text-align: left;
  width: 100%;
}
.venue-title {
  color: #000;
  font-size: 14px;
  font-weight: 600;
  padding-left: 10px;
}
.venue-distance {
  color: #000;
  font-size: 12px;
  font-weight: 500;
  padding-left: 10px;
}
</style>
