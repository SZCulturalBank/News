<template>
  <div class="tn-reader-paper container">

    <section class="row tn-board-head">
      <h3 class="ng-binding">{{title}}</h3>
      <div class="tn-head-info">
        <span class="time ng-binding">{{today}}</span>
        <span class="hor-sep"></span>
        <span class="brand ng-binding">{{author}}</span>
      </div>
      <hr>
    </section>

    <section class="row tn-article-body flex">
      <div class="left">
        <section class="title-l">
          <strong class="title-text">{{traditionalTextLeft}}</strong>
        </section>
      </div>
      <div class="right">
        <section class="title-l">
          <strong class="title-text">{{traditionalTextRight}}</strong>
        </section>
      </div>
    </section>

    <hr class="red">

    <section class="row tn-article-body flex" v-for="(item, index) in traditionalMedia" :key="index+'-1'">
      <div class="left">
        <img class="left-img" :src="item.picture" />
      </div>
      <div class="right">
        <a class="right-link" target="_blank" :href="item.link">
          {{item.text}}
        </a>
      </div>
    </section>

    <hr class="red">

    <section class="row tn-article-body flex margin45">
      <div class="left">
        <section class="title-l">
          <strong class="title-text">{{selfTextLeft}}</strong>
        </section>
      </div>
      <div class="right">
        <section class="title-l">
          <strong class="title-text">{{selfTextRight}}</strong>
        </section>
      </div>
    </section>

    <hr class="red">

    <section class="row tn-article-body flex" v-for="(item, index) in selfMedia" :key="index+'-2'">
      <div class="left">
        <img class="left-img" :src="item.picture" />
      </div>
      <div class="right">
        <a class="right-link" target="_blank" :href="item.link">
          {{item.text}}
        </a>
      </div>
    </section>

    <hr class="red">

    <section class="row tn-board-foot">
      <hr>
      <div class="col-xs-3 text-left no-padding">
        感谢阅读
        <!-- <span ng-bind="showInfo.hit_count | hitCountText" class="ng-binding">735</span> -->
      </div>
      <div class="col-xs-6 text-center no-padding">
        &nbsp;
      </div>
      <div class="col-xs-3 text-right no-padding">
        <!-- <a class="report-button" ng-href="/report/99016015" href="/report/99016015">
          举报
        </a> -->
        <a href="www.manfredhu.com">更多</a>
      </div>
    </section>

  </div>
</template>

<script>
import Axios from 'axios';
import Moment from 'moment';
export default {
  name: 'NewList',
  data() {
    return {
      selfTextLeft: '',
      selfTextRight: '',
      traditionalTextLeft: '',
      traditionalTextRight: '',
      author: '',
      title: '',
      date: '',

      traditionalMedia: [],
      selfMedia: []
    };
  },
  computed: {
    today: () => {
      return (
        this.date ||
        Moment()
          .format('L')
          .split('/')
          .reverse()
          .join('-')
      );
    }
  },
  mounted() {
    const self = this;
    Axios.get('News/static/db.json')
      .then(response => {
        const {
          title,
          date,
          author,
          selfTextLeft,
          selfTextRight,
          traditionalTextLeft,
          traditionalTextRight,
          traditionalMedia,
          selfMedia
        } = response.data;
        this.title = title;
        this.date = date;
        this.author = author;
        this.selfTextLeft = selfTextLeft;
        this.selfTextRight = selfTextRight;
        this.traditionalTextLeft = traditionalTextLeft;
        this.traditionalTextRight = traditionalTextRight;

        this.traditionalMedia = traditionalMedia;
        this.selfMedia = selfMedia;
      })
      .catch(function(error) {
        // handle error
        console.log(error);
      });
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.title-l,
.title-r {
  display: inline-block;
  padding: 4px;
  border: 1px solid rgb(223, 223, 223);
  font-size: 21px;
  letter-spacing: 0px;
  position: relative;
}
.title-l:before,
.title-r:before {
  content: '';
  width: 12px;
  height: 12px;
  border-top: 3px solid rgb(249, 110, 87);
  border-right: 3px solid rgb(249, 110, 87);
  position: absolute;
  right: -2px;
  top: -2px;
}
.title-l:after,
.title-r:after {
  content: '';
  width: 12px;
  height: 12px;
  border-bottom: 3px solid rgb(249, 110, 87);
  border-left: 3px solid rgb(249, 110, 87);
  position: absolute;
  left: -2px;
  bottom: -2px;
}
.title-text {
  padding: 2px 6px;
  border: 1px solid rgb(223, 223, 223);
}
.left {
  width: 35%;
  display: flex;
  justify-content: center;
}
.right {
  width: 65%;
  display: flex;
  justify-content: center;
}
.flex {
  display: flex;
  margin-top: 15px;
  margin-bottom: 15px;
}
.red {
  margin: 0.5em 0px;
  background-color: rgb(249, 110, 87);
  height: 1px;
  margin-left: -15px;
  margin-right: -15px;
}
.left-img {
  vertical-align: middle;
  width: auto;
  height: auto;
  max-width: 100%;
  max-height: 100%;
  margin: 15px 0;
}
.right-link {
  font-size: 14px;
  margin: 15px 0;
  padding: 0 6px;
}
.margin45 {
  margin-top: 45px;
}
</style>
