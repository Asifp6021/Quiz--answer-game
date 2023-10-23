we are going to create question and answer quizz app

1. ------------************ creating questions *****************-----------

added objects which has all data we are working on frontend show we don't have database for data.

that is why we are creating object and storing data in it.

and selected all the necessory elements to work with.

2. ------------------************* rendered quetion and choices and background image.  ********

const lastQuestion = questions.length - 1;
let activeQuestion = 0;
let count = 0; 

this is three variable i have created thik of it as state management js.

and using this i have created function rendered.

3.  -----------*********** render time progress ********

const questionTime = 10; // 10 seconds
const gaugeWidth = 800; // 800px <- this is the widh of the progress time bar and we have 10 seconds so i devided 800 / 10 = 80; each second 80px background color going to appear so user will have illusion that it is progressing.

const gaugeUnit = gaugeWidth / questionTime; //80px


---------------------

function renderProgress() {
    for (let questionIndex = 0; questionIndex < lastQuestion; questionIndex++) {
        progressContainer.innerHTML += "<div class='progress-box' id=" + questionIndex + "></div>"
    }
} and we have 10 box because we have 10 question it shows progress of user. in the game.

5.   -----------*********** adding timeCounter ********

function renderTimecounter() {
    if (count <= questionTime) {
        counter.innerHTML = count;
        timeGauge.style.width = count * gaugeUnit + "px";

        count++;
    } else {
        count = 0;
    } 

    here is if count reaches 10 then again i made it 0 in else part.

    and i am going to add this function in timeIntervel. so i can run this code each second

    6.   -----------*********** grabbing user's selected answer ********

    i am using forEach loop to keep track of all choices. and adding eventlistener on each one if user clicks any of one.

    remember we can know where user has clicked using e.target. so we want to grab innerText because innerText is answer.

       6.   -----------*********** checking whether answer is right or not ********

    function checkAnswer(answer) {
    if (answer === questions[activeQuestion].correctAnswer) {
        score++;
        answerIsCorrect();
    } else {
        answerIsIncorrect();
    }
}

if (answer === questions[activeQuestion].correctAnswer) <- first i am checking on which question user is corrently present. then checking that comparing that questions correct answer with the user's selected answer.


7.   -----------*********** moving to next quetion ********

1. doesn't matter if selected answer is right or wrong i want to move to next quetion. that is why within checkAnswer function i called nextQuestion.

2. and also if user not able to give answer in 10 seconds. then also i moved to next question. and consider wrong answer for which user have not given answer.

that is why i called nextquetion and checkIsIncorrect withing timeCounter function.