# Module 07: Project - Interactive Quiz

## Level 2.3: JavaScript Basics

---

## 🎯 Project Overview

Combine everything you've learned to build an **Interactive Quiz Application**!

---

## Project Requirements

### Must Have (Required)

| Requirement | Skills Demonstrated |
|-------------|---------------------|
| ✅ Multiple questions (5+) | Arrays, objects |
| ✅ Multiple choice answers | DOM manipulation |
| ✅ Track score | Variables, logic |
| ✅ Show current question number | Loops, counters |
| ✅ Correct/incorrect feedback | Conditionals |
| ✅ Final results screen | DOM, template literals |
| ✅ Restart functionality | Functions, reset |
| ✅ Styled with your CSS | HTML/CSS skills |

### Nice to Have (Bonus)

| Feature | Skills Shown |
|---------|--------------|
| ⭐ Timer per question | setInterval, async |
| ⭐ Progress bar | DOM, CSS |
| ⭐ Animations | CSS transitions |
| ⭐ High score tracking | localStorage |
| ⭐ Category selection | Advanced logic |
| ⭐ Sound effects | Audio API |

---

## Project Structure

```
quiz-app/
├── index.html
├── css/
│   └── style.css
└── js/
    └── app.js
```

---

## Step 1: HTML Structure

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cambodia Knowledge Quiz</title>
    <link rel="stylesheet" href="css/style.css">
</head>
<body>
    <div class="quiz-container">
        <!-- Start Screen -->
        <div id="start-screen" class="screen">
            <h1>🇰🇭 Cambodia Quiz</h1>
            <p>Test your knowledge about Cambodia!</p>
            <button id="start-btn" class="btn btn-primary">Start Quiz</button>
        </div>

        <!-- Quiz Screen -->
        <div id="quiz-screen" class="screen hidden">
            <div class="quiz-header">
                <span id="question-number">Question 1/10</span>
                <span id="score">Score: 0</span>
            </div>
            
            <div class="quiz-body">
                <h2 id="question">Question text here?</h2>
                <div id="answers" class="answers">
                    <!-- Answers will be inserted here -->
                </div>
            </div>
            
            <div class="quiz-footer">
                <button id="next-btn" class="btn" disabled>Next Question</button>
            </div>
        </div>

        <!-- Result Screen -->
        <div id="result-screen" class="screen hidden">
            <h1>Quiz Complete!</h1>
            <div id="final-score"></div>
            <p id="result-message"></p>
            <button id="restart-btn" class="btn btn-primary">Play Again</button>
        </div>
    </div>

    <script src="js/app.js"></script>
</body>
</html>
```

---

## Step 2: CSS Styling

```css
/* css/style.css */

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Segoe UI', Tahoma, sans-serif;
    background: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 20px;
}

.quiz-container {
    background: white;
    border-radius: 16px;
    box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
    max-width: 600px;
    width: 100%;
    overflow: hidden;
}

.screen {
    padding: 40px;
    text-align: center;
}

.hidden {
    display: none !important;
}

/* Start Screen */
#start-screen h1 {
    font-size: 2.5rem;
    margin-bottom: 15px;
    color: #1e3c72;
}

#start-screen p {
    color: #666;
    margin-bottom: 30px;
}

/* Buttons */
.btn {
    padding: 15px 40px;
    font-size: 1rem;
    border: none;
    border-radius: 8px;
    cursor: pointer;
    transition: transform 0.2s, box-shadow 0.2s;
}

.btn:hover:not(:disabled) {
    transform: translateY(-2px);
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
}

.btn:disabled {
    opacity: 0.5;
    cursor: not-allowed;
}

.btn-primary {
    background: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
    color: white;
}

/* Quiz Screen */
.quiz-header {
    display: flex;
    justify-content: space-between;
    margin-bottom: 30px;
    color: #666;
    font-size: 0.9rem;
}

#question {
    font-size: 1.5rem;
    color: #333;
    margin-bottom: 30px;
    line-height: 1.4;
}

.answers {
    display: flex;
    flex-direction: column;
    gap: 12px;
}

.answer-btn {
    padding: 15px 20px;
    text-align: left;
    background: #f8f9fa;
    border: 2px solid #e9ecef;
    border-radius: 8px;
    cursor: pointer;
    transition: all 0.2s;
    font-size: 1rem;
}

.answer-btn:hover {
    border-color: #1e3c72;
    background: #f0f4ff;
}

.answer-btn.correct {
    background: #d4edda;
    border-color: #28a745;
    color: #155724;
}

.answer-btn.wrong {
    background: #f8d7da;
    border-color: #dc3545;
    color: #721c24;
}

.answer-btn:disabled {
    cursor: not-allowed;
}

.quiz-footer {
    margin-top: 30px;
}

/* Result Screen */
#final-score {
    font-size: 4rem;
    font-weight: bold;
    color: #1e3c72;
    margin: 20px 0;
}

#result-message {
    font-size: 1.2rem;
    color: #666;
    margin-bottom: 30px;
}

/* Responsive */
@media (max-width: 480px) {
    .screen {
        padding: 25px;
    }
    
    #start-screen h1 {
        font-size: 2rem;
    }
    
    #question {
        font-size: 1.2rem;
    }
}
```

---

## Step 3: JavaScript Logic

```javascript
// js/app.js

// Quiz Questions
const questions = [
    {
        question: "What is the capital of Cambodia?",
        answers: ["Siem Reap", "Phnom Penh", "Battambang", "Sihanoukville"],
        correct: 1
    },
    {
        question: "Which ancient temple complex is Cambodia famous for?",
        answers: ["Borobudur", "Angkor Wat", "Bagan", "Ayutthaya"],
        correct: 1
    },
    {
        question: "What is the official language of Cambodia?",
        answers: ["Thai", "Vietnamese", "Khmer", "Lao"],
        correct: 2
    },
    {
        question: "Which river is the most important in Cambodia?",
        answers: ["Mekong River", "Amazon River", "Nile River", "Yangtze River"],
        correct: 0
    },
    {
        question: "What currency does Cambodia use?",
        answers: ["Thai Baht", "Vietnamese Dong", "Cambodian Riel", "US Dollar only"],
        correct: 2
    },
    {
        question: "In which year did Cambodia gain independence from France?",
        answers: ["1945", "1953", "1960", "1975"],
        correct: 1
    },
    {
        question: "What is the national animal of Cambodia?",
        answers: ["Elephant", "Tiger", "Kouprey", "Dragon"],
        correct: 2
    },
    {
        question: "Which lake in Cambodia is known as the largest freshwater lake in Southeast Asia?",
        answers: ["Tonle Sap", "Lake Victoria", "Lake Toba", "Inle Lake"],
        correct: 0
    }
];

// State variables
let currentQuestion = 0;
let score = 0;
let answered = false;

// DOM Elements
const startScreen = document.getElementById("start-screen");
const quizScreen = document.getElementById("quiz-screen");
const resultScreen = document.getElementById("result-screen");
const startBtn = document.getElementById("start-btn");
const nextBtn = document.getElementById("next-btn");
const restartBtn = document.getElementById("restart-btn");
const questionEl = document.getElementById("question");
const answersEl = document.getElementById("answers");
const questionNumberEl = document.getElementById("question-number");
const scoreEl = document.getElementById("score");
const finalScoreEl = document.getElementById("final-score");
const resultMessageEl = document.getElementById("result-message");

// Event Listeners
startBtn.addEventListener("click", startQuiz);
nextBtn.addEventListener("click", nextQuestion);
restartBtn.addEventListener("click", restartQuiz);

// Functions
function startQuiz() {
    startScreen.classList.add("hidden");
    quizScreen.classList.remove("hidden");
    showQuestion();
}

function showQuestion() {
    answered = false;
    nextBtn.disabled = true;
    
    const question = questions[currentQuestion];
    
    // Update question number and score
    questionNumberEl.textContent = `Question ${currentQuestion + 1}/${questions.length}`;
    scoreEl.textContent = `Score: ${score}`;
    
    // Show question
    questionEl.textContent = question.question;
    
    // Clear previous answers
    answersEl.innerHTML = "";
    
    // Create answer buttons
    question.answers.forEach((answer, index) => {
        const button = document.createElement("button");
        button.textContent = answer;
        button.classList.add("answer-btn");
        button.addEventListener("click", () => selectAnswer(index));
        answersEl.appendChild(button);
    });
}

function selectAnswer(selectedIndex) {
    if (answered) return;
    answered = true;
    
    const question = questions[currentQuestion];
    const buttons = answersEl.querySelectorAll(".answer-btn");
    
    // Disable all buttons
    buttons.forEach(btn => btn.disabled = true);
    
    // Show correct/wrong
    if (selectedIndex === question.correct) {
        buttons[selectedIndex].classList.add("correct");
        score++;
        scoreEl.textContent = `Score: ${score}`;
    } else {
        buttons[selectedIndex].classList.add("wrong");
        buttons[question.correct].classList.add("correct");
    }
    
    // Enable next button
    nextBtn.disabled = false;
    
    // Change button text for last question
    if (currentQuestion === questions.length - 1) {
        nextBtn.textContent = "See Results";
    }
}

function nextQuestion() {
    currentQuestion++;
    
    if (currentQuestion < questions.length) {
        showQuestion();
    } else {
        showResults();
    }
}

function showResults() {
    quizScreen.classList.add("hidden");
    resultScreen.classList.remove("hidden");
    
    const percentage = Math.round((score / questions.length) * 100);
    finalScoreEl.textContent = `${score}/${questions.length}`;
    
    let message = "";
    if (percentage === 100) {
        message = "🎉 Perfect! You're a Cambodia expert!";
    } else if (percentage >= 80) {
        message = "🌟 Excellent! You know Cambodia well!";
    } else if (percentage >= 60) {
        message = "👍 Good job! Keep learning!";
    } else if (percentage >= 40) {
        message = "📚 Not bad! There's more to learn.";
    } else {
        message = "🔍 Keep exploring Cambodia!";
    }
    
    resultMessageEl.textContent = message;
}

function restartQuiz() {
    currentQuestion = 0;
    score = 0;
    nextBtn.textContent = "Next Question";
    
    resultScreen.classList.add("hidden");
    startScreen.classList.remove("hidden");
}
```

---

## Step 4: Add More Questions

Expand your questions array with more topics:

- History
- Geography
- Culture
- Food
- Famous people

---

## Evaluation Criteria

| Criteria | Points |
|----------|--------|
| **Functionality** (40) | |
| Questions display correctly | 10 |
| Answer selection works | 10 |
| Score tracking accurate | 10 |
| Results show at end | 10 |
| **Code Quality** (30) | |
| Clean, organized code | 10 |
| Meaningful variable names | 10 |
| Functions used properly | 10 |
| **Design** (20) | |
| Visual appeal | 10 |
| Responsive design | 10 |
| **Extras** (10) | |
| Additional features | 10 |

---

## 🎓 Level Complete

Upon completing this project:

✅ **JavaScript Basics Badge** earned
✅ **JavaScript Developer Certificate** awarded
✅ Ready for **Level 2.4: JavaScript Advanced** or **Level 2.5: Git & GitHub**

---

<div align="center">

**You built your first JavaScript app!** 🎉

*This quiz will grow with you — add new features as you learn!*

🇰🇭

</div>
