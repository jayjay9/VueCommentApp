<template>
  <div class="comment-container" @mouseover="hover=true" @mouseleave="hover=false">
    <div class="image wrapper">
      <img :src="img" alt="Profile pic"/>
    </div>
    <div class="details wrapper">
        <div class="user-info">
          <span class="name">{{userName}}</span>
          <div class="subtitle type">{{userType}}</div>
          <span class="date subtitle">{{postedDate}}</span>
        </div>
        <div class="comment">
          {{commentText}}
        </div>
        <div class="actions subtitle" :class="{active: hover}">
          <span>Reply</span>
          <span class="replies">
            <span class="number">{{numberOfReplies}}</span>
              Replies
            </span>
          <span><i class="fa fa-angle-up" aria-hidden="true" v-on:click="addVote"></i>{{totalUpvotes}}</span>
          <span><i class="fa fa-angle-down" aria-hidden="true" v-on:click="removeVote"></i>{{totalDownvotes}}</span>
        </div>
      </div>
    </div>
</template>

<script>
export default {
  name: 'Comment',
  data() {
    return {
      img: 'https://images.unsplash.com/photo-1519098901909-b1553a1190af?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&w=1000&q=80',
      userName: 'Brad',
      userType: 'Author',
      commentText: 'So what the German automaker is likely to focus on today is the bigger picture. This will be the first time we see the Taycan free from any prototype bodywork.',
      postedDate: '2 minutes ago',
      numberOfReplies: 21,
      upvotes: 123,
      downvotes: 0,
      upvote: 0,
      downvote: 0,
      hover: false
    }
  },
  computed: {
    totalUpvotes: function() {
      return this.upvotes + this.upvote;
    },
    totalDownvotes: function() {
      return this.downvotes + this.downvote;
    }
  },
  methods: {
    addVote() {
      this.upvote = 1;
      this.downvote = 0;
    },
    removeVote() {
      this.upvote = 0;
      this.downvote = -1;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.comment-container {
  display: flex;
  border-bottom: 1px solid rgba(0, 0, 0, .1);
  border-top: 1px solid rgba(0, 0, 0, .1);
  padding: 25px 10px 10px 10px;
}

.wrapper {
  display: inline-block;
}

img {
  border-radius: 50%;
  height: auto;
  width: 100%;
}

.image {
  width: 10%;
}

.details {
  padding-left: 20px;
  width: 90%;
}

.details div {
  margin-bottom: 6px;
}

.name, .number, .type {
  font-weight: bold;
}

.subtitle {
  color: grey;
  font-size: 11px;
  text-transform: uppercase;
}

.actions > span {
  margin-right: 15px;
}

i {
  font-size: 16px;
  margin-right: 5px;
}

.type {
  background-color: black;
  border-radius: 10px;
  color: white;
  display: inline-block;
  font-weight: bold;
  margin: 0 8px;
  padding: 0 12px;
}

.active {
  color: black;
}
</style>
