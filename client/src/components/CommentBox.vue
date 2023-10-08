<template>
  <div class="commentBox">
    <b-row class="m-0">
      <div class="user">
        <p>{{ comment.username }}</p>
      </div>
      <div id="ifEdited" v-if="comment.isEdited">
        <p class="editedText">(edited)</p>
      </div>
      <div class="date">
        <p>Posted on {{ comment.date }}</p>
      </div>
    </b-row>
    <div class="opinion">
      <b-row v-if="comment.opinion === true">
        <img
          src="../assets/agree.png"
          class="agreeIcon"
          alt="agree"
          width="30"
          height="30"
        />
        <p class="test">Agree</p>
      </b-row>
      <b-row v-if="comment.opinion === false">
        <img
          src="../assets/disagree.png"
          class="disagreeIcon"
          alt="disagree"
          width="30"
          height="30"
        />
        <p class="test">Disagree</p>
      </b-row>
    </div>
    <div class="comment">
      <p v-if="this.showMore">
        {{ comment.text }}
      </p>
      <p v-else>{{ comment.text.slice(0, 200) }}</p>
      <b-button
        :pressed="this.showMore"
        v-if="comment.text.length > 200"
        v-on:click="showComment()"
        class="showMoreBtn"
        text
      >
        {{ this.showMore ? 'Show less' : 'Show more' }}
      </b-button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'comment-item',
  props: ['comment'],
  data() {
    return {
      showMore: false
    }
  },
  methods: {
    showComment() {
      this.showMore = !this.showMore
    }
  }
}
</script>

<style scoped>
.commentBox {
  border: 1px solid black;
  border-radius: 10px;
  padding: 10px;
  background-color: #fff;
  word-wrap: break-word;
  width: 40%;
  margin-left: 55%;
  margin-top: 50px;
  position: relative;
  text-overflow: ellipsis;
}
.user {
  display: inline-block;
  font-size: 1em;
  color: black;
  border: 1px solid black;
  border-radius: 10px;
  margin: 10px;
  padding: 10px;
  width: auto;
  height: 50px;
  background-color: #f5f5f5;
  margin-right: auto;
}
.comment {
  font-size: 1em;
  color: black;
  border: 1px solid black;
  border-radius: 10px;
  margin: 10px;
  padding: 10px;
  width: auto;
  height: auto;
  background-color: #f5f5f5;
}
.showMoreBtn {
  width: 120px;
  height: 30px;
  font-size: 1em;
  padding: 3px;
  color: black;
  border: 1px solid black;
  border-radius: 10px;
  background-color: white;
}
.date {
  font-size: 1em;
  margin: 10px;
  padding: 10px;
  height: 50px;
  margin-left: auto;
}
.editedText {
  font-size: 0.8em;
  margin: 10px;
  padding: 10px;
  height: 50px;
}
.opinion {
  margin-left: 30px;
}

.test {
  margin-left: 5px;
}

@media screen and (max-width: 1200px) {
  .commentBox {
    width: 80%;
    margin-left: 10%;
  }
  .user {
    font-size: 0.8em;
  }
}
@media screen and (max-width: 576px) {
  .commentBox {
    width: 90%;
    margin-left: 5%;
  }
  .user {
    font-size: 0.8em;
    margin-right: 0px;
  }
  .date {
    margin-left: 0px;
  }
}
</style>