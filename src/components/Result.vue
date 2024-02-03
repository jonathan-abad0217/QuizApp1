<template>
  <div class="result">
    <div class="title">{{ results[resultIndex].title }}</div>
    <div class="desc">{{ this.totalCorrect }}/{{ questions.length }}</div>
    <div class="desc-1">
      {{ results[resultIndex].desc }}
    </div>

    <div v-for="(question, index) in questions" :key="index">
      <div class="result-question">{{ question.q }}</div>
      <div class="user-answer">
        User's Answer: {{ getUserResponse(question, index) }}
      </div>
      <div class="correct-answer">
        Correct Answer: {{ getCorrectAnswer(question) }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["results", "totalCorrect", "userResponses", "questions"],
  computed: {
    resultIndex() {
      let index = 0;

      this.results.forEach((item, indexNum) => {
        if (item.min <= this.totalCorrect && item.max >= this.totalCorrect) {
          index = indexNum;
        }
      });

      return index;
    },
  },
  methods: {
    getCorrectAnswer(question) {
      return question.answers.find((answer) => answer.is_correct).text;
    },

    getUserResponse(question, index) {
      // Access the user's selected answer object
      const userResponse = this.userResponses[index];

      if (userResponse) {
        // Return the text of the user's selected answer
        return userResponse.text;
      } else {
        return "No answer selected"; // Handle cases where the user hasn't answered
      }
    },
  },
};
</script>
