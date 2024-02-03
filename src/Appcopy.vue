<template>
  <div class="ctr">
    <questions
      v-if="questionsAnswered < questions.length"
      :questions="questions"
      :questionsAnswered="questionsAnswered"
      @question-answered="questionAnswered"
    ></questions>
    <result
      v-else
      :results="results"
      :totalCorrect="totalCorrect"
      :userResponses="userResponses"
      :questions="questions"
    ></result>

    <button
      type="button"
      class="reset-btn"
      @click.prevent="reset"
      v-if="this.questionsAnswered === questions.length"
    >
      Reset
    </button>
  </div>
</template>

<script>
import Questions from "./components/Questions.vue";
import Result from "./components/Result.vue";
export default {
  name: "App",
  components: {
    Questions,
    Result,
  },
  data() {
    return {
      questionsAnswered: 0,
      totalCorrect: 0,
      userResponses: [],
      questions: [
        {
          q: "This refers to the collective assessment of a brand's trustworthiness, credibility, and overall standing within a community, industry, or society. It reflects the qualitative judgements people make about the brand based on its past actions and behavior.",
          answers: [
            {
              text: "Brand Perceptions",
              is_correct: false,
            },
            {
              text: "Brand Perception",
              is_correct: false,
            },
            {
              text: "Brand Relations",
              is_correct: false,
            },
            {
              text: "Brand Reputation",
              is_correct: true,
            },
          ],
        },
        {
          q: "In the principles of effective communication, this stands for the ability to communicate clearly and straightforwardly using simple and diirect language that is easy to understand.",
          answers: [
            {
              text: "Correctness",
              is_correct: false,
            },
            {
              text: "Coherence",
              is_correct: false,
            },
            {
              text: "Clarity",
              is_correct: true,
            },
            {
              text: "Courtesy",
              is_correct: false,
            },
            {
              text: "Confidence",
              is_correct: false,
            },
          ],
        },
        {
          q: "In the principles of effective communication, this refers 'to the ability to communicate with assurance and conviction by speaking in a powerful, self-assured way that projects a sense of belief.'",
          answers: [
            {
              text: "Conciseness",
              is_correct: false,
            },

            {
              text: "Coherence",
              is_correct: false,
            },

            {
              text: "Courtesy",
              is_correct: false,
            },
            {
              text: "Confidence",
              is_correct: true,
            },
            {
              text: "Clarity",
              is_correct: false,
            },
            {
              text: "Corectness",
              is_correct: false,
            },
          ],
        },
        {
          q: "This refers to the overall perception that consumers have about a brand. It's the mental picture people form when thinking about the brand, encompassing visual elements, personality traits, and consumer associations.",
          answers: [
            {
              text: "Brand Relations",
              is_correct: false,
            },
            {
              text: "Brand Image",
              is_correct: true,
            },
            {
              text: "Brand Reputation",
              is_correct: false,
            },
            {
              text: "Brand Perception",
              is_correct: false,
            },
          ],
        },
        {
          q: "This is the process of conveying a message in a way that is understood and has the intended impact. It involves transmitting information clearly and accurately, and it goes beyond just the transmission of words-it encompasses the ability to engage, influence, and create shared understanding between the sender and the receiver.",
          answers: [
            {
              text: "Clear Communication",
              is_correct: false,
            },
            {
              text: "Affective Communication",
              is_correct: false,
            },
            {
              text: "Effective Communication",
              is_correct: true,
            },
            {
              text: "Advance Communication",
              is_correct: false,
            },
          ],
        },
        {
          q: "In the principle of effective communication, this refers to the ability to organize and present information in a logical and orderly manner.",
          answers: [
            {
              text: "Correctness",
              is_correct: false,
            },
            {
              text: "Confidence",
              is_correct: false,
            },
            {
              text: "Conciseness",
              is_correct: false,
            },
            {
              text: "Clarity",
              is_correct: false,
            },
            {
              text: "Coherence",
              is_correct: true,
            },
            {
              text: "Courtesy",
              is_correct: false,
            },
          ],
        },
        {
          q: "It is a strategic communication process that organizations/business or individuals use to build and maintain positive relationships with the public. The gola of this is to create a positive image and reputation, enhance visibility, and establish mutual understunding between an entity and its target audience, which may include customers, employees, investors, media, government agencies, and the general public.",
          answers: [
            {
              text: "Public Relations",
              is_correct: true,
            },
            {
              text: "Client Relations",
              is_correct: false,
            },
            {
              text: "Human Relations",
              is_correct: false,
            },
            {
              text: "Customer Relations",
              is_correct: false,
            },
          ],
        },
        {
          q: "This is the relationship that specifically pertains to the interaction between a business and its individual customers and client base.",
          answers: [
            {
              text: "Client Relations",
              is_correct: false,
            },
            {
              text: "Human Relations",
              is_correct: false,
            },
            {
              text: "Public Relations ",
              is_correct: false,
            },
            {
              text: "Customer Relations",
              is_correct: true,
            },
          ],
        },
        {
          q: "In the principles of effective communication, this refers to the accuracy and appropriateness of the language and information used in communication by using proper grammar, spelling and punctuation and providing accurate and reliable information.",
          answers: [
            {
              text: "Confidence",
              is_correct: false,
            },
            {
              text: "Courtesy ",
              is_correct: false,
            },
            {
              text: "Coherence",
              is_correct: false,
            },
            {
              text: "Correctness",
              is_correct: true,
            },
            {
              text: "Clarity",
              is_correct: false,
            },
            {
              text: "Conciseness ",
              is_correct: false,
            },
          ],
        },
        {
          q: "In the principles of effective communication, this refers to the ability to maintain a logical flow of information and ideas.",
          answers: [
            {
              text: "Conciseness ",
              is_correct: false,
            },
            {
              text: "Correctness",
              is_correct: false,
            },
            {
              text: "Clarity",
              is_correct: false,
            },
            {
              text: "Courtesy ",
              is_correct: false,
            },
            {
              text: "Confidence",
              is_correct: false,
            },
            {
              text: "Coherence",
              is_correct: true,
            },
          ],
        },
        {
          q: "This is the relationship that specifically pertains to the interaction between a business and its employees.",
          answers: [
            {
              text: "Human Relations",
              is_correct: false,
            },
            {
              text: "Customer Relations",
              is_correct: true,
            },
            {
              text: "Public Relations ",
              is_correct: false,
            },
            {
              text: "Client Relations",
              is_correct: false,
            },
          ],
        },
        {
          q: "In the principle of effective communication, this refers to the ability to communicate the message in as few words as possible without sacrificing clarity or completeness.",
          answers: [
            {
              text: "Courtesy",
              is_correct: false,
            },
            {
              text: "Correctness",
              is_correct: false,
            },
            {
              text: "Confidence",
              is_correct: false,
            },
            {
              text: "Conciseness",
              is_correct: true,
            },
            {
              text: "Coherence",
              is_correct: false,
            },
            {
              text: "Clarity",
              is_correct: false,
            },
          ],
        },
        {
          q: "In the principles of effective communication, this refers to the ability to communicate politely and respectfully by using appropriate language, tone, and non-verbal cues and considering the audience's perspective and needs.",
          answers: [
            {
              text: "Coherence",
              is_correct: false,
            },
            {
              text: "Correctness",
              is_correct: false,
            },
            {
              text: "Conciseness ",
              is_correct: false,
            },
            {
              text: "Confidence",
              is_correct: false,
            },
            {
              text: "Clarity",
              is_correct: false,
            },
            {
              text: "Courtesy",
              is_correct: true,
            },
          ],
        },
        {
          q: "This refers to the emotional response or connection a consumer has with a brand. It’s how the brand resonates with the consumer on an emotional level.",
          answers: [
            {
              text: "Brand Relations",
              is_correct: false,
            },
            {
              text: "Brand Perception",
              is_correct: true,
            },
            {
              text: "Brand Image",
              is_correct: false,
            },
            {
              text: "Brand Reputation",
              is_correct: false,
            },
          ],
        },
        {
          q: "This is the process of communicating in a way that is clear, concise, and easy to understand. It involves using simple language, avoiding jargon, and ensuring that the message is not ambiguous or confusing.",
          answers: [
            {
              text: "Clear Communication",
              is_correct: true,
            },
            {
              text: "Advance Communication",
              is_correct: false,
            },
            {
              text: "Affective Communication",
              is_correct: false,
            },
            {
              text: "Effective Communication",
              is_correct: false,
            },
          ],
        },
      ],
      results: [
        {
          min: 0,
          max: 7,
          title: "Try again!",
          desc: "Do a little more studying and you may succeed!",
        },
        {
          min: 8,
          max: 11,
          title: "Wow, you're good!",
          desc: "Keep up the good work!",
        },
        {
          min: 12,
          max: 15,
          title: "You're a genius!",
          desc: "Studying has definitely paid off for you!",
        },
      ],
    };
  },
  methods: {
    questionAnswered(answer) {
      this.userResponses.push(answer);
      if (answer.is_correct) {
        this.totalCorrect++;
      }
      this.questionsAnswered++;
    },
    reset() {
      this.questionsAnswered = 0;
      this.totalCorrect = 0;
      this.userResponses = [];
    },
  },
};
</script>

<style></style>
