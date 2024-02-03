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
          q: "Sorting similar and related business transactions into the three categories of assets, liabilities, and owner’s equity.",
          answers: [
            {
              text: "Classifying",
              is_correct: true,
            },
            {
              text: "Recording",
              is_correct: false,
            },
            {
              text: "Interpreting",
              is_correct: false,
            },
            {
              text: "Summarizing",
              is_correct: false,
            },
          ],
        },
        {
          q: "Representing the qualitative and quantitative financial information about the business transactions in a language comprehensible to the users of financial statements . By interpreting the data in the financial statements, users are able to determine the financial standing of the company as well as its stability and growth potential. Users interpret financial information relating to specific business decisions. This makes accounting the language of business.",
          answers: [
            {
              text: "Classifying",
              is_correct: false,
            },
            {
              text: "Recording",
              is_correct: false,
            },
            {
              text: "Interpreting",
              is_correct: true,
            },
            {
              text: "Summarizing",
              is_correct: false,
            },
          ],
        },
        {
          q: "Writing down of business transactions chronologically in the books of account as they transpire.",
          answers: [
            {
              text: "Classifying",
              is_correct: false,
            },
            {
              text: "Recording",
              is_correct: true,
            },
            {
              text: "Interpreting",
              is_correct: false,
            },
            {
              text: "Summarizing",
              is_correct: false,
            },
          ],
        },

        {
          q: "Organizational managers use financial information to set goals for their companies. Managers evaluate their progress towards these goals and use financial data as a guide for future management actions.",
          answers: [
            {
              text: "Employees",
              is_correct: false,
            },
            {
              text: "Financial Institutions/Creditors",
              is_correct: false,
            },
            {
              text: "Management",
              is_correct: true,
            },
            {
              text: "Investors/Owners/Stockholders",
              is_correct: false,
            },
            {
              text: "Government",
              is_correct: false,
            },
          ],
        },
        {
          q: "Financial information provide information on company stability which is important for employees to determine if they have a future in the company.",
          answers: [
            {
              text: "Employees",
              is_correct: true,
            },
            {
              text: "Financial Institutions/Creditors",
              is_correct: false,
            },
            {
              text: "Management",
              is_correct: false,
            },
            {
              text: "Investors/Owners/Stockholders",
              is_correct: false,
            },
            {
              text: "Government",
              is_correct: false,
            },
          ],
        },
        {
          q: "These people provide the financial resources to keep the business going. These parties decide whether to invest or not depending on the estimated amount of income on their investments. Upon investments, they would want to know the financial position or resultof operations of their business investment.",
          answers: [
            {
              text: "Employees",
              is_correct: false,
            },
            {
              text: "Financial Institutions/Creditors",
              is_correct: false,
            },
            {
              text: "Management",
              is_correct: false,
            },
            {
              text: "Investors/Owners/Stockholders",
              is_correct: true,
            },
            {
              text: "Government",
              is_correct: false,
            },
          ],
        },
        {
          q: "It employs both historical and estimated datas in assisting management with day-to-day problems and planning for the future.",
          answers: [
            {
              text: "Tax accounting",
              is_correct: false,
            },
            {
              text: "General or financial accounting",
              is_correct: false,
            },
            {
              text: "Management Accounting",
              is_correct: true,
            },
            {
              text: "International accounting",
              is_correct: false,
            },
            {
              text: "Cost Accounting",
              is_correct: false,
            },
            {
              text: "Auditing",
              is_correct: false,
            },
          ],
        },
        {
          q: "It involves the preparation of tax return and the consideration of tax consequences of proposed business transactions.",
          answers: [
            {
              text: "Cost Accounting",
              is_correct: false,
            },
            {
              text: "General or financial accounting",
              is_correct: false,
            },
            {
              text: "Budgetary Accounting",
              is_correct: false,
            },
            {
              text: "Social accounting",
              is_correct: false,
            },
            {
              text: "No-for-profit accounting",
              is_correct: false,
            },
            {
              text: "Tax accounting",
              is_correct: true,
            },
          ],
        },
        {
          q: "This is a Service type business, which of the following is not? ",
          answers: [
            {
              text: "Barber Shop ",
              is_correct: false,
            },
            {
              text: "Laundry Shop",
              is_correct: false,
            },
            {
              text: "Shoe Factory",
              is_correct: true,
            },
            {
              text: "Dental Clinic ",
              is_correct: false,
            },
            {
              text: "Repair Shop",
              is_correct: false,
            },
          ],
        },
        {
          q: "This is a Manufacturing type business, which of the following is not?",
          answers: [
            {
              text: "Shoe Factory",
              is_correct: false,
            },
            {
              text: "Furniture Maker",
              is_correct: false,
            },
            {
              text: "Car Assembler",
              is_correct: false,
            },
            {
              text: "Department Store",
              is_correct: true,
            },
            {
              text: "Textile Mills",
              is_correct: false,
            },
          ],
        },
        {
          q: "This is a Merchandising type business, which of the following is not?",
          answers: [
            {
              text: "Courtesy",
              is_correct: false,
            },
            {
              text: "Department Store",
              is_correct: false,
            },
            {
              text: "Hardware",
              is_correct: false,
            },
            {
              text: "Laundry Shop",
              is_correct: true,
            },
            {
              text: "Grocery",
              is_correct: false,
            },
            {
              text: "Fruit Stand",
              is_correct: false,
            },
          ],
        },
        // Lesson 1 End
        // Lesson 2 Start
        {
          q: "Are stock and bonds purchased by the enterprise and are to be held for only a short span of time or short duration. They are usually purchased when a business has excess cash.",
          answers: [
            {
              text: "Cash",
              is_correct: false,
            },
            {
              text: "Prepaid Expenses",
              is_correct: false,
            },
            {
              text: "Accumulated Depreciation  ",
              is_correct: false,
            },
            {
              text: "Contra-Asset Accounts",
              is_correct: false,
            },
            {
              text: "Marketable Securities",
              is_correct: true,
            },
          ],
        },
        {
          q: "Is a ability to pay the bank or other financing institution arising from funds borrowed by the business from these institution payable within twelvemonths or shorter.",
          answers: [
            {
              text: "Notes Payable",
              is_correct: false,
            },
            {
              text: "Brand Relations",
              is_correct: false,
            },
            {
              text: "Loan Payable",
              is_correct: true,
            },
            {
              text: "Accounts Payable",
              is_correct: false,
            },
            {
              text: "Utilities Payable",
              is_correct: false,
            },
          ],
        },
        {
          q: "Includes all payments made to employees or workers for rendering services to the company. Examples are salaries or wages, 13th month pay, cost of living allowances, and other related benefits given to them.",
          answers: [
            {
              text: "Salaries or Wages Expenses",
              is_correct: true,
            },
            {
              text: "Insurance Expense",
              is_correct: false,
            },
            {
              text: "Supplies Expense",
              is_correct: false,
            },
            {
              text: "Utilities Expense",
              is_correct: false,
            },
          ],
        },
        {
          q: "Non-monetary assets without physical substance held for use in the production or supply of goods, for rental to others, or for administrative purposes e.g., goodwill, patents, copyright.",
          answers: [
            {
              text: "Furniture and fixtures",
              is_correct: false,
            },
            {
              text: "Accumulated depreciation ",
              is_correct: false,
            },
            {
              text: "Intangible assets",
              is_correct: true,
            },
            {
              text: "Equipment",
              is_correct: false,
            },
          ],
        },
        {
          q: "Typewriter, air-conditioner, calculator, filing cabinet, computer, electric fan, trucks, cars used in business.",
          answers: [
            {
              text: "Furniture and fixtures",
              is_correct: false,
            },
            {
              text: "Accumulated depreciation ",
              is_correct: false,
            },
            {
              text: "Intangible assets",
              is_correct: false,
            },
            {
              text: "Equipment",
              is_correct: true,
            },
          ],
        },
        {
          q: "Contra-asset account representing expired cost of property, plant, and equipment as a result of usage and passage of time.",
          answers: [
            {
              text: "Land",
              is_correct: false,
            },
            {
              text: "Intangible assets",
              is_correct: false,
            },
            {
              text: "Equipment",
              is_correct: false,
            },
            {
              text: "Accumulated depreciation",
              is_correct: true,
            },
          ],
        },
        {
          q: "Which of the following is not a Income Statement Item",
          answers: [
            {
              text: "Interest receivable",
              is_correct: true,
            },
            {
              text: "Interest expense",
              is_correct: false,
            },
            {
              text: "Supplies Expense",
              is_correct: false,
            },
            {
              text: "Miscellaneous Expense",
              is_correct: false,
            },
          ],
        },
        {
          q: "Which of the following is not a Balance Sheet Item",
          answers: [
            {
              text: "Drawing account",
              is_correct: false,
            },
            {
              text: "Account Payable",
              is_correct: false,
            },
            {
              text: "Interest Income",
              is_correct: true,
            },
            {
              text: "Mortgage payable",
              is_correct: false,
            },
          ],
        },
        {
          q: "Amount owed to others for expenses already incurred but not yet paid.",
          answers: [
            {
              text: "Utilities payable ",
              is_correct: false,
            },
            {
              text: "Accrued liabilities",
              is_correct: true,
            },
            {
              text: "Notes payable",
              is_correct: false,
            },
            {
              text: "Account payable",
              is_correct: false,
            },
          ],
        },
        {
          q: "Debts arising from purchase of an asset on account evidenced by a promissory note.",
          answers: [
            {
              text: "Utilities payable ",
              is_correct: false,
            },
            {
              text: "Accrued liabilities",
              is_correct: false,
            },
            {
              text: "Notes payable",
              is_correct: true,
            },
            {
              text: "Account payable",
              is_correct: false,
            },
          ],
        },
        // Lesson 2 End
        // Lesson 4 Start
        {
          q: "It is the first book of account.",
          answers: [
            {
              text: "Journalizing ",
              is_correct: false,
            },
            {
              text: "Trial Balance",
              is_correct: false,
            },
            {
              text: "Journal",
              is_correct: true,
            },
            {
              text: "Posting ",
              is_correct: false,
            },
            {
              text: "Accounting Cycle",
              is_correct: false,
            },
            {
              text: "Ledger",
              is_correct: false,
            },
          ],
        },
        {
          q: "It is the book of final entry.",
          answers: [
            {
              text: "Accounting Cycle",
              is_correct: false,
            },
            {
              text: "Trial Balance",
              is_correct: false,
            },
            {
              text: "Journalizing ",
              is_correct: false,
            },

            {
              text: "Posting ",
              is_correct: false,
            },
            {
              text: "Ledger",
              is_correct: true,
            },
            {
              text: "Journal",
              is_correct: false,
            },
          ],
        },

        {
          q: "The uniform procedure done to accomplish the accounting process.",
          answers: [
            {
              text: "Ledger",
              is_correct: false,
            },
            {
              text: "Trial Balance",
              is_correct: false,
            },
            {
              text: "Accounting Cycle",
              is_correct: true,
            },

            {
              text: "Posting ",
              is_correct: false,
            },

            {
              text: "Journalizing ",
              is_correct: false,
            },
            {
              text: "Journal",
              is_correct: false,
            },
          ],
        },
        {
          q: "Process of recording transaction in the journal.",
          answers: [
            {
              text: "Journal",
              is_correct: false,
            },
            {
              text: "Ledger",
              is_correct: false,
            },
            {
              text: "Accounting Cycle",
              is_correct: false,
            },
            {
              text: "Trial Balance",
              is_correct: false,
            },

            {
              text: "Journalizing ",
              is_correct: true,
            },

            {
              text: "Posting ",
              is_correct: false,
            },
          ],
        },
        {
          q: "The process of transferring information from the journal to the ledger.",
          answers: [
            {
              text: "Posting ",
              is_correct: true,
            },
            {
              text: "Journal",
              is_correct: false,
            },
            {
              text: "Trial Balance",
              is_correct: false,
            },

            {
              text: "Accounting Cycle",
              is_correct: false,
            },

            {
              text: "Journalizing ",
              is_correct: false,
            },
            {
              text: "Ledger",
              is_correct: false,
            },
          ],
        },
        {
          q: "It is a list of accounts found in the ledger together with account’s balance.",
          answers: [
            {
              text: "Posting ",
              is_correct: false,
            },
            {
              text: "Journal",
              is_correct: false,
            },

            {
              text: "Accounting Cycle",
              is_correct: false,
            },

            {
              text: "Journalizing ",
              is_correct: false,
            },
            {
              text: "Trial Balance",
              is_correct: true,
            },
            {
              text: "Ledger",
              is_correct: false,
            },
          ],
        },
        {
          q: "Which of the following accounting cycle is correct: The trial balance is a list of accounts found in the ledger together with the accounts balance or total. This is a proof that for every debit, there is a corresponding credit. Hence, it is also a proof that the ledger is in balance.",
          answers: [
            {
              text: "Preparing the financial statements",
              is_correct: false,
            },
            {
              text: "Recording transactions in the journal",
              is_correct: false,
            },

            {
              text: "Preparing the trial balance",
              is_correct: true,
            },

            {
              text: "Preparing the worksheet and adjusting entries",
              is_correct: false,
            },
            {
              text: "Preparing the post closing trial balance",
              is_correct: false,
            },
          ],
        },
        {
          q: "A statement of financial position, income statement, statement of changes in owner’s equity, and statement of cash flows are prepared to provide useful information to parties interested in the financial information of the business.",
          answers: [
            {
              text: "Preparing the financial statements",
              is_correct: true,
            },
            {
              text: "Posting journal entries to the ledger",
              is_correct: false,
            },

            {
              text: "Journalizing and posting of closing journal entries",
              is_correct: false,
            },

            {
              text: "Preparing the trial balance",
              is_correct: false,
            },
            {
              text: "Preparing the worksheet and adjusting entries",
              is_correct: false,
            },
          ],
        },
        {
          q: "Closing entries are prepared at the end of the accounting period to update the owner’s capital account. This will also eliminate the balances of the nominal accounts so that they may be ready for the next period.",
          answers: [
            {
              text: "Posting journal entries to the ledger ",
              is_correct: false,
            },
            {
              text: "Journalizing and posting of adjusting journal entries",
              is_correct: false,
            },

            {
              text: "Journalizing and posting of reversing journal entries ",
              is_correct: false,
            },

            {
              text: "Journalizing and posting of closing journal entries",
              is_correct: true,
            },
            {
              text: " Preparing the worksheet and adjusting entries",
              is_correct: false,
            },
          ],
        },
        // Lesson 4 End
      ],
      results: [
        {
          min: 0,
          max: 14,
          title: "Try again!",
          desc: "Do a little more studying and you may succeed!",
        },
        {
          min: 15,
          max: 23,
          title: "Wow, you're good!",
          desc: "Keep up the good work!",
        },
        {
          min: 24,
          max: 30,
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
